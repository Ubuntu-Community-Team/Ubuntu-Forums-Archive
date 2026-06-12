---
title: "blender"
date: 2008-12-04
forum: Art &amp; Design
---

### Post by chips24 on 2008-12-04
i have the interface figured out, but when i add a texture, lighting, reflectivity, etc, the preview displays the changes, but the render and the object do not update the changes, neither shaded mode or textured mode, im i doing something wrong?
 
thanks for the help.

---

### Post by hessiess on 2008-12-04
Can you post a .blend by any chance?

---

### Post by chips24 on 2008-12-04
no. i dont have an internet connection on my computer, im using a school computer for the internet.

---

### Post by chips24 on 2008-12-05
im trying to say that i cant get my 3d object to look like the preview in textured mode or shaded mode.

---

### Post by lavinog on 2008-12-06
It will be pretty tough to help you without more info.
Can you give details on steps to recreate the scenario (start with cube...apply cloud texture...press this button...etc)

Blender is pretty tough to learn without some outside help...since you don't have an internet connections I would recommend buying a book on blender at a bookstore..._The Essential Blender_ is a good one to start with. I just recently bought _Bounce, Tumble, and Splash!_. It has been updated for version 2.46 and explains the physics and particle engine including the new hair tools.

---

### Post by lavinog on 2008-12-06
Can you describe how the rendered image is different?
is it too dark, shiny...wrong color...

---

### Post by kayosiii on 2008-12-06
I am guessing that you are using uvmapped image textures --  you are right this does not automatically work in the renderer.
In the buttons panel go to materials and make sure that your mesh has a material set if not then you can create a new one. tweek you will mostly likely need to add a texture to the material - make the texture an image texture and load the image that you are using in the viewport. then go back to the material settings and make sure that the image is mapped to UV (look for ma input). You can then tweek the material settings to get the material closer to what you want. You can even use other textures to make some parts of the object more shiny than others.

---

### Post by chips24 on 2008-12-11
> **kayosiii said:**
> I am guessing that you are using uvmapped image textures -- you are right this does not automatically work in the renderer.
In the buttons panel go to materials and make sure that your mesh has a material set if not then you can create a new one. tweek you will mostly likely need to add a texture to the material - make the texture an image texture and load the image that you are using in the viewport. then go back to the material settings and make sure that the image is mapped to UV (look for ma input). You can then tweek the material settings to get the material closer to what you want. You can even use other textures to make some parts of the object more shiny than others.
 
how? the only way i can make a  texture display is if i got the the object button and press "add Multires" over and over again
 
I was trying to adjust the reflectivity and the translucency, the little box with a preview shows the changes, but my object that i created doesnt match the preview, im trying to make a realistic island with buildings on it, but it look so blah with out the addons.

---

### Post by chips24 on 2008-12-11
> **lavinog said:**
> Can you describe how the rendered image is different?
is it too dark, shiny...wrong color...
 
no changes will take affect if ajust the translusency or the reflectvity, the only changes that take affect are the colours.

---

### Post by chips24 on 2008-12-13
suuggestions?

---

### Post by lavinog on 2008-12-13
can you copy screenshots to a flash drive and post them? or copy the blend file to a flash drive and post it?

---

### Post by chips24 on 2009-05-01
i forgot ithat i was supposed to press "F12" :lolflag:

---

