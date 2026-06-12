---
title: "[SOLVED] GIMP newb question"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by drunkardivan on 2007-12-06
I can't believe I have to ask this, but I do:

How do I combine two images in the GIMP? I've got my picture of Fred Thompson, I've got my picture of a pimp hat (with feather). How do I combine these, so Fred's wearing the pimp hat (with feather)?

---

### Post by kebes on 2007-12-06
I'm not sure what level of detail you want in the instructions, but try something like this:


**1.** Open the picture of the person, and the picture of the hat (File > Open).

**2.** On the main picture (the person), create a new layer (Layers > New Layer).

**3.** Go to the picture of the hat (using select tool), select the hat, and copy to clipboard (Edit > Copy).

**4.** Go to the main picture, make sure you have the new empty layer selected, and paste (Edit > Paste). On the "Layers" panel you should click the anchor icon to merge the paste into your new layer.

**5.** You will now have the hat overlayed over the person. You then trim that layer so that only the hat is showing. There are multiple ways of doing this:
 a. You can just select the eraser tool and erase the border bits (you can switch between a sharp or fuzzy eraser to get the edge to look right).
 b. Or, you can use the lasso select tool, and select the border areas, and use Ctrl+X to cut away those regions. Do this until you get the hat all by itself.
 c. Or, you can carefully select the entire hat, invert the selection (Select > Invert) and cut away the border that way (this lets you feather the selection (Select > Feather) before cutting, so that you can get a nice edge).
 d. There are other ways, but you get the idea...

**6.** Now that you have a hat without any border, you can move the hat to the right location using the move tool (looks like crossed arrows) and change the size using the scale tool (when using the scale tool, make sure you constrain the aspect ratio so that hat doesn't end up looking distorted). You may also need to rotate the hat. Position the hat where you need it to be.

**7.** You're done! You can save the image as a standard jpg or png or whatever (File > Save As).


There are of course other subtleties if you want it to look better (you might want to adjust color or blur on each layer so that they look like they were photographed together), but this should get you started.

Hope that helps.

---

### Post by drunkardivan on 2007-12-06
Thanks. For some reason, GIMP wouldn't paste between two, but adding a third, blank image worked.

---

