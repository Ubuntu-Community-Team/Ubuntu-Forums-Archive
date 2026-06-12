---
title: "Gimp selection modes: I am confused"
date: 2008-11-09
forum: Art &amp; Design
---

### Post by Browser_ice on 2008-11-09
In my moving to Linux, I got rid of a lot of Windows software. In doing this I used to have Photoshop but now I am forcing myself to use Gimp.

One thing which is confusing me a lot is the selection modes in Gimp.

It seams that even if I do a selection, once I am done, I can see the selection borders being inside another selection and I do not know how to make my selection baked into the image after something I have done.

Ex: doing a perspective manipulation on a selection area (partial image selection). When the perspective is done, that selection is still active. I do not know how to remove that manual selection I did to bake the resulted transformation into the rest of the image. I tried doing a Selection None or All but I still see 2 selection areas: mine and the canvas one. The resulted transformation becomes a floating selection layer.

In photoshop, I selected an area did a transform on it and applied it. It was baked into the rest of the image. 

I know I must not work with Gimp in terms of applying work on it like I used to do with Photoshop.

---

### Post by eightmillion on 2008-11-09
After you do the transformation, you should have *Floating Selection (Transformation)* among your layers. You can right click on it and either select _N_ew Layer to make it its own layer or you can select Merge Do_w_n to anchor it to the layer that you are working on.

---

### Post by oedipuss on 2008-11-10
Or you can grab a selection tool, and click anywhere outside the selection. The pointer should have an anchor emblem to indicate that clicking means drop or merge down. 
The yellow dashed rectangle is the layer boundaries, it hasn't got anything to do with selections. It just shows up because the floating layer is smaller than the others, as it is cropped to contain the selection only. Right click on a layer to see some options on modifying it; for instance Layer to image size scales the layer boundary to the full image. You can hide it completely [menu View/Show layer boundary] but it's useful sometimes.

A little unrelated thing that might help: if you want to move the selected part of an image instead of the selection rectangle itself, hold down ctrl+alt and drag. 
At least, it took *me* a while to figure that out :P
Kind of unfortunate that most of the default compiz shortcuts use ctrl+alt drag, and completely override that :P

---

### Post by alfu on 2009-12-23
**[COLOR="Red"]To move a selection in Gimp, you have to draw a markee <R> around a region and then hold down both <CTL> and <ALT> before LMB dragging it.[/COLOR]**

Since I often save quick schema as .gif files, moving a selection is probably the most frequent operation I do in a paint program.  To have to hold down two modifier keys is incredibly cumbersome -- I can't understand why that layer of complexity had to be added to something I thought was totally nailed down since the invention of the wheel: select something and just drag the damned thing.

Does anyone know if there is a config file somewhere that I can edit to change this back to the way it should be?

**Space bar to move the canvas:** I like the way you can use the spacebar like in PhotoShop to move the canvas, but why does the resulting action have to be so dodgy? (Maybe this doesn't happen on your computer, but on mine the canvas just wanders around at random when the spacebar is pushed)

@ Exodist: Thank you for the tip.  Philosophically I am opposed to having to navigate to a toolbox to do something that should be done much more fluidly (you don't go to a toolbox to move a chair across the room, do you?), so I assumed there was an easier way.

---

### Post by Exodist on 2009-12-23
> **alfu said:**
> **[COLOR=Red]To move a selection in Gimp, you have to draw a markee <R> around a region and then hold down both <CTL> and <ALT> before LMB dragging it.[/COLOR]**

Since I often save quick schema as .gif files, moving a selection is probably the most frequent operation I do in a paint program.  To have to hold down two modifier keys is incredibly cumbersome..................

You must have something setup to prevent normal moving. Most of us just click on the move tool and it does not matter what layer you have selected as it will grab it. So you have to be careful and make sure it is the layer you wanted moving.


@ OP, easy way to make the pasted image a layer is to just simple click the new layer button.

---

