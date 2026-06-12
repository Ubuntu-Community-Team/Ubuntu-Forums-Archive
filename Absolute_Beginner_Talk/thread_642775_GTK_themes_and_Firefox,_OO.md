---
title: "GTK themes and Firefox, OO"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by MattP220 on 2007-12-17
Hello,

I'm very new to Linux, so this question will probably be trivial to fix (bear with me, I'm recovering from Windows). 

I'm using Ubuntu 7.10, and I've installed a theme using GTK2. Everything works perfectly in terms of execution. However it causes OO to stop using icons (with text placeholders instead), and as this is a very dark theme it makes some webpages display white on white. Neither is a dealbreaker, but both are annoying.

My question is, is there any way I can stop these two applications from using the GTK theme so as to fix the display issues?

---

### Post by Dynaflow on 2007-12-17
I've had that happen before too, and I think it has to do with the particular icon set your theme is using.  I always find that going into System -> Preferences -> Appearance, clicking the Customize button for my selected theme, and having it use another icon set works to restore icons to OO Word (which I use as my acid test).  Tangerine and Mist, for example, don't seem to cause me any problems, but Crystal SVG always seems to screw things up in Open Office.  Experiment around.

---

### Post by MattP220 on 2007-12-17
Hmmm...tried that out w/ every icon set I have installed (default or otherwise), and no luck.

---

### Post by Dynaflow on 2007-12-17
What theme is it?  Is it something from the Art Manager program in Ubuntu, or is it something you got from gnome-look.org?

---

### Post by MattP220 on 2007-12-18
This came from gnome-look.org

[http://www.gnome-look.org/content/show.php/Divinorum?content=65533](http://www.gnome-look.org/content/show.php/Divinorum?content=65533)

I followed his instructions to alter the OO background, which worked fine, but the icon set just...isn't there, no matter which I use.

---

### Post by JurB on 2007-12-18
Did you also install "gtk2-engines-pixbuf" as instructed?

---

### Post by MattP220 on 2007-12-18
I wasn't sure, so I just tried it again from the terminal as per instructions...it went through the installation process and spit this out:

sudo apt-get install gtk2-engines-pixbuf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtk2-engines-pixbuf is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

