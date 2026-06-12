---
title: "Another Error again!!!"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by oblivioncth on 2008-03-25
When I try to turn on visual effects I get this message (see picture). How do I fix it? I appreciate any help  :)

---

### Post by joshrobinson on 2008-03-25
are you running an ati card?

---

### Post by codeslicer on 2008-03-25
That dialog isn't really specific.... we need to extract some more information.

Go to Applications->Accessories->Terminal. Then, copy this:

```
gnome-appearance-properties
```

into the terminal. Make sure you don't try to use Keyboard shortcuts in the terminal - they don't work and are used for other things like terminating a program(Only in the terminal, not in the whole Ubuntu)

After running it, try to enable the effects again. If it doesn't work, switch back to the terminal window and copy all that info here.

---

### Post by oblivioncth on 2008-03-25
Sorry.


Yes I am running an ATI card an I took a screen shot of the terminals response when I try to 
enable them with that code.

---

### Post by joshrobinson on 2008-03-25
could you post the results to the following command
```
fglrxinfo
```

---

### Post by misterhead on 2008-03-25
what ATI card are you using?

---

### Post by om1 on 2008-03-25
do you have your restricted drivers enabled?

---

### Post by SunnyRabbiera on 2008-03-25
you may have to face the possibility that desktop effects may not work with your card, are the effects vital to you?

---

### Post by BL00dFox on 2008-03-25
Have you got your restricted drivers enabled?

Run:
```
glxinfo
```

and see whether it says DIRECT RENDERING: YES at the top

---

### Post by codeslicer on 2008-03-25
Try changing the driver to an ATI driver in System->Administration->Screens and Graphics. Make sure to click Test before applying, otherwise you might not be able to boot into your desktop!

---

### Post by oblivioncth on 2008-03-25
Ok...
 Here is the result for the code: 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6473 (8.37.6)


As it says I running an ATI Radeon X1950 Series

I tried to configure the option to set the graphics setting for my card in System>Administration>Screen and Graphics. I made it ATI | Radeon and hit test and the screen went black so im guessing it didn't work. The were a bunch of Radeons with () that I didn't under stand. I took a screen shot.

And yes my restricted driver is enabled

---

### Post by oblivioncth on 2008-03-25
Im running a ATI Radeon X1950 Series.

This is the results for that code:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6473 (8.37.6)


Yes I have my restricted driver enabled.

And when I went to change my settings in System>Administration> Screen and graphics I don't know which Radeon to select(view screen shot).

EDIT: Sorry for double posting. I forgot there was a second page so when I saw my post wasn't on the first page I thought it failed to post.

---

