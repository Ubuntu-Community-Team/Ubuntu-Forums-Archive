---
title: "PSD Files"
date: 2009-10-10
forum: Art &amp; Design
---

### Post by Majorflam on 2009-10-10
Is there any way to work with psd files in Ubuntu?

---

### Post by coldReactive on 2009-10-10
GIMP can open them, but it's hard to extract the data from them. I've tried it once.

And, Adjustment layers are not viewable by GIMP.

---

### Post by Fzang on 2009-10-10
GIMP can open them but it can only show normal layers. Special Photoshop layer styles and templates will be ignored on GIMP.

Short answer: no

---

### Post by ad_267 on 2009-10-10
Or you could install Photoshop using WINE. Check the Wine AppDB to see which versions work.

---

### Post by Incendia on 2009-10-12
> **ad_267 said:**
> Or you could install Photoshop using WINE. Check the Wine AppDB to see which versions work.

I do this; works fine. Photoshop CS3:

[B]What works
[/B]Installer
All menus and their functions
All tools and their functions 
All editing
Registration / Activation 
If fonts are too small for your liking at first go to
Edit > Preferences > General... 
Set UI font size to large 

[B]What does not
[/B]Occasionally hides the active project requiring one to go to Window > Arrange > New window for
This appears to be an issue with the Compiz cube 
Occasionally complains about inadequate permissions. I've always fixed this by restarting GDM 
sudo killall gdm
sudo gdm
Adobe Updater
The browse function 

[B]What was not tested
[/B]Updating the program

---

### Post by vinutux on 2009-10-13
> **Incendia said:**
> I do this; works fine. Photoshop CS3:

[B]What works
[/B]Installer
All menus and their functions
All tools and their functions 
All editing
Registration / Activation 
If fonts are too small for your liking at first go to
Edit > Preferences > General... 
Set UI font size to large 

[B]What does not
[/B]Occasionally hides the active project requiring one to go to Window > Arrange > New window for
This appears to be an issue with the Compiz cube 
Occasionally complains about inadequate permissions. I've always fixed this by restarting GDM 
sudo killall gdm
sudo gdm
Adobe Updater
The browse function 

[B]What was not tested
[/B]Updating the program


mmm..........what about cs4

---

### Post by kayosiii on 2009-10-13
Basically Adobe was fairly open with the photoshop file format up until version 6 so 3rd party applications will generally work with any feature that was in version 6 of photoshop. For more recent features I don't think you are going to have a lot of joy with any non Adobe product.

---

### Post by alex.rayu on 2009-10-13
CS4 will work well once you install it in wine 1.1.16, and then update wine to latest. Still, on some machines some functions will be unavailable, like docking of panels. Also, for some video cards, compiz will have to be disabled.

---

