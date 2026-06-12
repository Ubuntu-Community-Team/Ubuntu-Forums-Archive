---
title: "help with wacom in wine ps7"
date: 2007-05-23
forum: Art &amp; Design
---

### Post by ryankent on 2007-05-23
The problem is my tablet works fine in gimp and krita but in photoshop 7 it tries to erase when I use the brush tool, and if I turn my pen around and use the eraser side it tries to zoom in. none of the tools work but it recognizes the location of where my pen is. I have ps7 installed through wine. When photoshop launches a dialog comes up and says something about not being able to load photoshops interface fonts (but I copied my windows fonts over to ~/.wine/windows/fonts, so i dunno why that comes up), and another error after comes up after saying the UI font could not be loaded and I should exit and install it.  

I dont understand. If I use the mouse all the tools work fine. I thought it may be something with my xorg.conf but everything else works fine with my wacom, so then I think it's something with wine, but I'm not sure. I'm using the latest version of wine (wine-0.9.37) and a wacom intuos3. Please don't comment about using gimp, I have used gimp and I still do, I even used it on windows before ubuntu, but it doesn't cut it for me. and Krita is a little weird too, since I cant pick dpi and theres no hotkeys for brushes (I like krita better than gimp though).

any help would be appreciated

---

### Post by graigsmith on 2007-05-24
i doubt this would ever work.   Just because the wacom tablet is working with your linux apps doesn't mean it will ever work with photoshop in wine.  Wine would probably need some sort of translation mechanism.  Because the drivers are not wacom's drivers. they are made by the linux wacom project. the way the software or wacom drivers interface with programs is probably totally different.

---

### Post by graigsmith on 2007-05-24
hmm, though one person on this page seems to have pressure sensitivity working in wine. he diddn't give any clues to how he got it working, he just said it worked. 
[http://appdb.winehq.org/appview.php?iVersionId=1336](http://appdb.winehq.org/appview.php?iVersionId=1336)

---

### Post by ryankent on 2007-05-24
would there be a way to put in my wacom disc and install the drivers in wine? so that itll work in wine

---

### Post by ryankent on 2007-05-29
ok so its a problem with photoshop, not wine. with my wacom ps7 makes all my tools try to use the eraser, but with the mouse everything works fine. i tried cs2 and my tablet works great, but when i try to use any shortcuts it crashes. this is really annoying, i just need any version of ps to work. cs1 just crashes when it boots from not enough memory too. ps7 is so far the most stable but i need my tablet to work. help please :S

---

### Post by ubuntu.daemon on 2007-05-29
well I could suggest xara xtreme, lol works really well for editing, im trying to figure out on getting the picture editor out, cant seem to find it.....   :(

---

