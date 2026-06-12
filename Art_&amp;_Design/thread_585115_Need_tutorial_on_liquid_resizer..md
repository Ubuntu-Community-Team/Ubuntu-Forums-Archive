---
title: "Need tutorial on liquid resizer."
date: 2007-10-21
forum: Art &amp; Design
---

### Post by exploder on 2007-10-21
Can someone tell me step by step how to use liquid resizer in Gimp or point me to a step by step guide? I really want to use this tool. I want to remove a small section in the middle of an image.

Thanks in advance!

---

### Post by exploder on 2007-10-21
Anyone?

---

### Post by smartboyathome on 2007-10-21
I would help you if I knew what you were talking about, but I don't.

---

### Post by bashveank on 2007-10-21
He's talking about this 
[http://stuporglue.org/](http://stuporglue.org/)
I don't know how to use it either, unfortunately.

---

### Post by exploder on 2007-10-22
I am still seeking help on this. I have a Gimp Splash screen that I want to remove the version number and it's shadow from.

---

### Post by smartboyathome on 2007-10-23
> **exploder said:**
> I am still seeking help on this. I have a Gimp Splash screen that I want to remove the version number and it's shadow from.

you can use the smart remove plugin for the gimp. It is in the repositories. Simply select what you want to remove, and use Script-fu > Enhance > Smart remove

---

### Post by Oldster on 2007-10-23
You could crop the splash screen and then use the liquid rescale to stretch it back to size.

Open the liquid rescale plug in, click on the "chain link" next to the width and height entries to look open (unlock aspect ratio),  set the original width and height, and click OK.

That is one slick plugin.:)

---

### Post by exploder on 2007-10-23
How can I crop where the version number is? Here is the image I want to use.

[http://www.gnome-look.org/content/show.php/Murrivell+GIMP+glossy?content=49727](http://www.gnome-look.org/content/show.php/Murrivell+GIMP+glossy?content=49727)

The version number is wrong for Gutsy and if it can be removed it can be used with future versions. The creator of the splash sent me the source, but I do not know enough to do anything with it yet...

---

### Post by Oldster on 2007-10-23
Sorry, the version of liquid rescale I have wont do that..

---

### Post by Oldster on 2007-10-23
Smart Boyathome has the answer. So I learned something too.:)

Install the "gimp-resynthesizer" package. Open your picture. Put a box around what you want removed with the select tool.  Use "Script-fu > Enhance > Smart remove". Click Okay.

Info here:
[http://www.logarithmic.net/pfh/resynthesizer/removal]("http://www.logarithmic.net/pfh/resynthesizer/removal")

My attempt at it. Not perfect.

---

### Post by exploder on 2007-10-23
Oldster, you are a genius! Also your attemp to fix this looks pretty darn good! Thanks!

I will give this a try also.

---

### Post by exploder on 2007-10-23
I gave it a try and it fixed it perfectly! You would never know a version number was tgere. Thanks so much!

---

### Post by Oldster on 2007-10-24
FYI! I just found a little info on the use of the new liquid rescale plugin.

More fun with Gimp! :)

[http://meetthegimp.org/liquid-rescale-new-version-of-plugin/]("http://meetthegimp.org/liquid-rescale-new-version-of-plugin/")

---

### Post by exploder on 2007-10-25
Nice find! I will have to play with this!

---

