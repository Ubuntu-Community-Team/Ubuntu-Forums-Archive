---
title: "How do I make this background transparent?"
date: 2007-02-09
forum: Art &amp; Design
---

### Post by jincast90 on 2007-02-09
Hello. I want to try and make some new icons for some of my applications. I am doing this in GIMP, but I am no champ at this. If you look at the image I have attached. It is a Firefox logo. The thing is instead of having a white background I want it to be transparent, otherwise it looks stupid in the menus. I tried :) So how do I turn the color from white to non existent?

Edit. I just realized it must be quite hard to see that the picture does have a white background since everywhere around the image is white. But trust me the picture is a white square with a Firefox logo in it.

---

### Post by AndyW on 2007-02-09
I just searched google and found this png:

I just realized this is a newer version of the icon. I hope it works!

---

### Post by jincast90 on 2007-02-10
> **AndyW said:**
> I just searched google and found this png:

I just realized this is a newer version of the icon. I hope it works!

Yes that is exactly what I need. Thank you. Now does anyone know how to get rid of the white background like the image AndyW posted did so I can do it to some other icons?

---

### Post by pveith on 2007-02-10
Use Gimp.
Step 0: load the picture
Step 1: Create a new layer.
Step 2: Activate the Backgroundlayer (where the actual pic is after loading).
Step 3: Use the "magic wand" selection tool to select the white background.
Step 4: Invert the selection.
Step 5: Cut the logo out.
Step 6: Activate the new layer from step 1.
Step 7: Paste the logo in the new layer.
Step 8: delete the background layer.
Step 9: Save the result.

That's it. I overdetailed the steps and this is probably not the shortest way to do this in gimp. But it works...

---

### Post by jincast90 on 2007-02-10
> **pveith said:**
> Use Gimp.
Step 0: load the picture
Step 1: Create a new layer.
Step 2: Activate the Backgroundlayer (where the actual pic is after loading).
Step 3: Use the "magic wand" selection tool to select the white background.
Step 4: Invert the selection.
Step 5: Cut the logo out.
Step 6: Activate the new layer from step 1.
Step 7: Paste the logo in the new layer.
Step 8: delete the background layer.
Step 9: Save the result.

That's it. I overdetailed the steps and this is probably not the shortest way to do this in gimp. But it works...

Yay It worked. Ok my method differed slightly from yours, but I probably would not have found out how to do it without your help. So thanks a lot!

---

### Post by ComplexNumber on 2007-02-10
> **pveith said:**
> Use Gimp.
Step 0: load the picture
Step 1: Create a new layer.
Step 2: Activate the Backgroundlayer (where the actual pic is after loading).
Step 3: Use the "magic wand" selection tool to select the white background.
Step 4: Invert the selection.
Step 5: Cut the logo out.
Step 6: Activate the new layer from step 1.
Step 7: Paste the logo in the new layer.
Step 8: delete the background layer.
Step 9: Save the result.

That's it. I overdetailed the steps and this is probably not the shortest way to do this in gimp. But it works...
the only problem with that method is that it leaves a white fringe around the logo when used on a dark background.



i suggest the following which is shorter and doesn't suffer from that aftereffect:
1) load gimp
2) go to the menu and select: filters -> colours -> add colour to alpha.
3) white is already selected so you don't need to select the colour, so just press 'OK'.
4 save it with the png extension.
various bits and bobs within the logo can seem like they take on the colour of the background colour, but that can be remedied by doing a rough cut of those affected areas and then pasting them back into log with the transparent background. 
here is one i made earlier:

---

### Post by pveith on 2007-02-10
Cool, that is a really short way to do this ComplexNumber. I agree that my method will leave some fringes to be cleared manually, if the pic has some antialiasing... Will try your method next time i need to get something transparent (which happen quite often)... Thanx for sharing...

---

### Post by ComplexNumber on 2007-02-10
> **pveith said:**
> Cool, that is a really short way to do this ComplexNumber. I agree that my method will leave some fringes to be cleared manually, if the pic has some antialiasing... Will try your method next time i need to get something transparent (which happen quite often)... Thanx for sharing...
i used to use a method similar to yours which involved using cutting around the image (using intelligent scissors etc), then making the background transparent. but when the image is (for example) black, it left a nasty black fringe around the image on a white/light background. recently i've been playing about with transparency. i haven't quite sussed everything out yet, but i'm slowly getting there. it definitely produces a cleaner result than the old method, though.

---

### Post by Aelfric5578 on 2007-02-11
What you can also do is instead of doing "Color to Alpha" you can apply a layer mask.  When it asks you what type of layer mask you want, pick "Grayscale copy of layer" and check the box "Invert Mask."

At first the icon will be translucent.  Right click on the layer in the layers tab.  Make sure "Edit Mask" is checked.  Play around with your levels (Layers->Colors->Levels) until you get a purely black and white image.  With this particular image, you will have to then fill in areas which are invisible (but shouldn't be) with a white brush.

---

