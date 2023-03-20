# PiCOMPOSITOR
PiCompositor is a layer-based compositing tool for TouchDesigner.

* Authored by: Pedram Sadegh-Beyki [PiTHEOREM](https://www.pitheorem.xyz)
* Version: 0.1 (Released on March 2023)
>   This tool is one of the subtools of [PiKit](https://pitheorem.xyz/pikit) toolkit which is currently under development.

---
## TABLE OF CONTENT
- [PiCOMPOSITOR](#picompositor)
  - [TABLE OF CONTENT](#table-of-content)
  - [HOW IS THIS TOOL HELPFUL?](#how-is-this-tool-helpful)
  - [WHAT IS PiCOMPOSITOR COMP?](#what-is-picompositor-comp)
  - [USER INTERFACE](#user-interface)
  - [IMPORTING LAYERs](#importing-layers)
  - [SELECTING LAYERs](#selecting-layers)
  - [ACTIVE LAYERs](#active-layers)
  - [PREVIEW PANEL](#preview-panel)
  - [PARAMETERS PANEL](#parameters-panel)
  - [COMPOSITION PARAMETERs](#composition-parameters)
  - [VISIBILITY TAGs](#visibility-tags)
  - [LOCK TAGS](#lock-tags)
  - [COLOR TAGs](#color-tags)
  - [NAMEs \& IDs](#names--ids)
  - [BLEND TAGs](#blend-tags)
  - [MASKING LAYERs](#masking-layers)
  - [DUPLICATING LAYERs](#duplicating-layers)
  - [DELETING LAYERs](#deleting-layers)
  - [EXTRACTING LAYERs](#extracting-layers)
  - [EXTRA TIPS](#extra-tips)
  - [KEYBOARD HOTKEYS](#keyboard-hotkeys)
  - [BUGs \& FUTURE DEVELOPMENT](#bugs--future-development)
  - [HOW TO SUPPORT](#how-to-support)
  - [FINAL WORDS](#final-words)
---

## HOW IS THIS TOOL HELPFUL?
By adding your TOPs into PiCompositorCOMP, you make them as LAYERs of a COMPOSITION, with a variety of parameters and functionalities that you can easily control such as:

* **Blending** (Opacity, Blend Modes, Masking)
* **Transformations** (Position, Rotation, Scale)
* **Rearranging** (Duplicating, Reordering, Hiding/Unhiding)
* **Selection** (Locking, Selection Sets)
* **Preview** (Solo mode, Mid-level Composite)

---
## WHAT IS PiCOMPOSITOR COMP?

First thing to know is that each PiCompositor component is a **COMPOSITION** (like an empty canvas identical to the 'Document' in Photoshop or 'Composition' in AfterEffects) that has a certain **resolution size, background color, transparency**, and some other parameters, while holding all the layers you wish to add and returns the final composited result as the output.

---
## USER INTERFACE

There are THREE panels within PiCOMPOSITOR interface.

**LAYERS LIST:**        The list of layers (Always visible)

[**PREVIEW Panel:**](#preview-panel)      The dual-screen display of the ACTIVE layer beside compositor's final OUTPUT

[**PARAMETERS Panel:**](#parameters-panel)   The panel for changing LAYERs or main COMPOSITION's parameters

---
## IMPORTING LAYERs

To add your layers, drag'n'drop your TOPs onto the LAYERS LIST. 

You can also add another PiCOMPOSITOR instance as a layer. (This way you can make layer groups by nesting multiple PiCOMPOSITORs into a master PiCOMPOSITOR.)

You can only add TOPs or PiCOMPOSITOR instances.

    WARNING:
    The layers are referenced by their op.id attribute. Meaning that if you cut/paste any of the imported TOPs within NETWORK EDITOR, the layer will lose the reference and you need to redefine the source by drag'n'dropping the new TOP onto the layer's **Source** parameter.

---
## SELECTING LAYERs

(LClick) on a layer's name to select a single layer

[Ctrl]+(LClick) on multiple names to add multiple layers to your selection

[Up] or [Down] keys to select the layer above or below

**!** Locked layers cannot be selected ([why?](#lock-tags))

**TIP:** You can create multiple selection groups via layers' COLOR tag ([how?](#color-tags))

---
## ACTIVE LAYERs

By selecting each layer, you set them as ACTIVE. 

When selecting multiple layers, the last one becomes the active layer. 

You can always check the ACTIVE layer from the name at the PARAMETERS Header.

By activating a layer:
* You can set its parameters from the Parameters Panel.
* You can preview the composited view upon that layer from the Preview Panel.

        To view the active layer only (SOLO mode), hold down the [alt] key while hovering on the layer in LAYERS LIST.

---
## PREVIEW PANEL

By selecting/activating each layer, the ACTIVE viewer updates by showing the composition upto that layer.

By holding down [alt] while hovering on any layer from LAYERS LIST, you can see that layer in isolation (SOLO view).

(LClick) on FINAL OUTPUT Preview to activate the COMPOSITION for parameter adjustments (in PARAMETERS PANEL).

You can also [extract](#extracting-layers) any of the viewers by (LClick) Drag'n'drop from the preview onto NETWORK EDITOR.

---
## PARAMETERS PANEL

Here you can adjust the parameters (transform, opacity, blend mode, etc.) for either the SELECTED layers or the main COMPOSITION.

[How to access Composition's OUTPUT parameters?](#composition-settings)

*When multiple layers are selected, any changes in PARAMETERS panel will apply on all of them.*

    You can copy and paste a layer's parameters via famous Copy/Paste hotkeys [ctrl+c][ctrl+v] 

---
## COMPOSITION PARAMETERs

To change the composition's settings inside PARAMETERs PANEL (such as output resolution, background color & transparency, or any post-transformations), you should ACTIVATE the compositor, by one of the following ways:

* (LClick) on the OUTPUT section of the PREVIEW PANEL
* (LClick) on the empty space of the LAYERS LIST
* (LClick) on the 'Name' header on the LAYERS LIST


---
## VISIBILITY TAGs

The eye icon at the first column on the list, defines the VISIBILITY tag of each layer.

(LClick) on the eye icon of each layer to toggles its VISIBILITY

*If there are multiple layers selected, toggle applies on all of them.*

(LClick) on 'V' at the columns header to toggle the VISIBILITY of ALL LAYERS

(RClick) on the eye icon of each layer, to toggle the SOLO mode

    SOLO toggle makes the current layer to be the only visibile layer by hiding all the other layers.
    
    You can switch back to the previous VISIBILITY state of retoggling their SOLO.
    
    You can hold [alt] while hovering on any layer in the LAYERS LIST, to temporarily solo-view that layer from PREVIEW PANEL.

---
## LOCK TAGS 
Lock tags help to protect layers from selection or parameter changing. i.e. When a layer is locked, you CANNOT select, delete, nor change its parameters. However you can still change the VISIBILITY or LOCK attribute for any locked layer.

The lock icon at the second column of the LAYERS LIST, defines the LOCK tag of each layer.

* (LClick) on the lock icon to toggle its LOCK
* (LClick) on 'L' at the column's header to toggle the LOCK for ALL LAYERS

*If there are multiple layers selected, Lock toggle applies on all of them.*

---
## COLOR TAGs
Color tags help to create multiple selection sets or selection groups.

The COLOR tag is defined as the colored box in the third column of the LAYERS LIST.

(LClick) on a color tag to pick from the ColorMenu.

*If there are multiple layers selected, Blend changes applies on all of them.*

(RClick) on a color tag to select all the layers sharing the hovering Color Tag.

    * While on the ColorMenu, you can preview each option by holding [alt] and hovering on it.

    * You can add your own color tags by appending a Name and RGB values to the 'ColorTags_Table' DAT inside the PiCOMPOSITOR COMP (under 'UI' annotation).


---
## NAMEs & IDs
Each layer has a unique identity defined by a Name as well as a number indicating its order in the LAYERS LIST.

You can reorder any layer by drag'n'drop on Layer's Name or number (#)

(LClick) on any layer's Name or ID (#) to select and activate the layer

(2xClick) on a name in LAYERS LIST to edit the name of a layer

(LClick) on 'Name' at the column's header to deselect all layers and refreshes the list

---
## BLEND TAGs

(LClick) on any layer's Blend column to change its blend mode from the BlendMenu.

(RClick) on any layer's Blend column to reset its Blend to default blending (OVER).
  
*If there are multiple layers selected, Blend changes applies on all of them.*

    * While on the BlendMenu, you can preview each option by holding down [alt] and hovering on it.
  

---
## MASKING LAYERs

You can apply layer masks from outside the PiCompositor by drag and dropping them (as a TOP) into the layer's 'Mask Layer' Parameter. 

You can also (RClick) drag any inactive LAYER from the LAYERS LIST onto the selected layer's 'Mask Layer' parameter.

*If multiple layers are selected, the new Mask Layer parameter will be applied on all of them.*


---
## DUPLICATING LAYERs

The double-square icon at the right side of each layer, duplicates that layer.

You can also duplicate using [Ctrl+d] keyboard shortcut.

*If there are multiple layers selected, the duplication applies on all of them.*

---
## DELETING LAYERs

(LClick) on the red 'X' icon at the right side of each layer, to delete that layer.

You can also press on **[Delete]** key to delete the selected layers.

*If there are multiple layers selected,the deletion applies on all of them.*

(LClick) on black 'X' at the columns header to **Delete ALL** the layers

Locked Layers are immune from being deleted.

    WARNING: 
    * Though you can undo deleting layers, please consider the risks of losing layer data as it 'might' return unwanted results.
    
    * By deleting a layer source TOP from NETWORK EDITOR, you destroy its corresponding LAYER from PiCompositor and you cannot undo that.***

---
## EXTRACTING LAYERs

You can extract layers from the PiCOMPOSITOR onto your NETWORK EDITOR - resulting in a selectTOP.

There are two ways to extract a layer:

* Extract selected layers by Dragging them from LAYERS LIST and Drop onto NETWORK EDITOR
* Extract the active layer by Dragging its preview from PREVIEW PANEL and Drop onto NETWORK EDITOR


**This extraction comes in two modes:** 
* **COMPOSITED extraction** (Default drag'n'drop):
    
    To extract selected layer composited downwards at any stage.
  
  
* **SOLO extraction** (Hold [alt] + drag'n'drop):

    To extract the layer only - in isolation.


---
---
## EXTRA TIPS 

* To change the default 'Fit' setting for new layers, go to 'I/O' page of PiCOMPOSITOR's main parameters.
* In case you wish to clear up some memory, you can clear the UNDO data via PiCOMPOSITOR's 'Clear Undo Memory' pulse parameter in I/O page.
* In case the LAYERS LIST stops updating or shows buggy layers, click on the 'Name' header to force cook the list.

---
## KEYBOARD HOTKEYS
The following hotkeys apply within PiCOMPOSITOR's User Interface.

* **[Ctrl+a]** Selects all the layers
* **[Ctrl+d]** Duplicates the selected layers
* **[Ctrl+c]** Copies the active layer's parameters to clipboard
* **[Ctrl+v]** Pastes parameter settings from the clipboard
* **[Delete]** Deletes the selected layers.
* **[up/down]** Changes the currently selected layer to the one above or below
* **Holding [alt]** on any list (LayersList, BlendMenu or ColorMenu) helps to temporarily preview that option.

---
## BUGs & FUTURE DEVELOPMENT

Just like any program, this one comes with bugs and errors as well. So to report your bug huntings: 
* [Post an issue on Github](https://github.com/pitheorem/PiCompositor/issues) 
* [Write me an email](mailto:pitheorem@gmail.com)

There are some features that I'm looking forward to implement for later versions:
+ Merging or Grouping Layers directly within the interface
+ Shy Tags for layers, making them hidable from LAYERS LIST.
+ Multi-layer relative parameter adjusting (currently any change on parameters will apply absolutely identical on all the selected layers)
+ Viewer Developments (this is a big one - setting your transformations directly within Preview Panel could be a life-saver)
+ Effects list for each layer.
+ Got a cool idea? [drop me an email.](mailto:pitheorem@gmail.com)

---
## HOW TO SUPPORT
In case you find this tool useful and you would want to back me on the mission, there are multiple ways to give financial or non-financial support.

[To make financial support please visit the link here.](https://pitheorem.xyz/picompositor#support)

Any non-financial supports are also greatly valued and much appreciated:
* Share the news about this tool on any social media you use and help me spread the voice.
* Follow me through social media profiles [Instagram](instgram.com/pitheorem) or [Twitter](twitter.com/pitheorem)
* Since social media platforms are algorithmically biased, I'd appreciate your likes, sharing or retweeting any of my artworks that you like.
* [Write me](mailto:pitheorem@gmail.com) on how this tool was helpful for you. I'd be grateful to know.
  
Thank you very much in advance! :)

---
## FINAL WORDS

That's all folks! 

Good luck to you with this tool, hope you enjoy using it. ;)

Feel free to [drop me an email](mailto:pitheorem@gmail.com) if you got any questions or suggestions.
