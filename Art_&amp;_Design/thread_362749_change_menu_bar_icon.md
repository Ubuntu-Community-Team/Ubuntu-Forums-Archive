---
title: "change menu bar icon"
date: 2007-02-16
forum: Art &amp; Design
---

### Post by Ryan8720 on 2007-02-16
I'm having trouble changing the icon next to Applications on the menu bar.  I've switched the distributor-logo.svg with my own in /usr/share/icons/Tango/scalable/places/. But now it is showing a pair of shoeprints instead of the Tux icon i replaced it with (it used to be the Ubuntu logo). What did I do wrong?

---

### Post by louis_nichols on 2007-02-16
The footprint thingy is shown whenever the file that si supposed to be there can not be loaded. So it might be that you forgot to place the file you want under /usr/share/icons/Tango/scalable/places/ or that you misspelled the name of the file. It is also possible that the file is not supported. I'm not sure what kind of image formats can be used, but SVG would be a sure thing...

---

### Post by ComplexNumber on 2007-02-16
> **Ryan8720 said:**
> I'm having trouble changing the icon next to Applications on the menu bar.  I've switched the distributor-logo.svg with my own in /usr/share/icons/Tango/scalable/places/. But now it is showing a pair of shoeprints instead of the Tux icon i replaced it with (it used to be the Ubuntu logo). What did I do wrong?
it depends upon the icon theme that you're using. sometimes a theme has its own icon for the menu. if it doesn't, it will 'inherit' the default from the default theme(on ubuntu, this is Human). the default can be found in 
/usr/share/icons/Human/scalable/places/start-here.svg




you need to look for the 'start-here' icon.

---

### Post by BobCFC on 2008-03-10
After going mad trying to do this myself then getting it working I thought I would post here.

For me replacing every start-here.svg on my system did nothing.

I have my own custom icon set built up in the .icons folder in my home directory (based on Tango with the blue Mist folder icons).  To change the menu logo I had to replace a file in the 24x24 folder not the scalable folder.

Maybe this is because my bars are set to 24 pixels high I thought they were on defaults.

Anyway create a PNG file called  start-here.png and put it in the 24x24 directory and it works.  You have to resize it otherwise if you put a 32pixel icon in the 24x24 directory it just makes your bar bigger.


TIP: you can reload the panel after you replace an icon to see if it works by typing **killall gnome-panel**

---

