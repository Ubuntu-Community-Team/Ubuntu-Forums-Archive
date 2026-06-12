---
title: "Flying/scrolling windows"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by MasterCylinder on 2008-04-16
I saw this video on YouTube and this guy has some tweek that let his windows scroll/fly, just like in Vista....

How do I do this? What is it called

---

### Post by Lolicon on 2008-04-16
You mean wobbly windows? If you're on Ubuntu you just have to enable desktop effects.

---

### Post by Tatty on 2008-04-16
System->Preferences->Appearance.  Then select what you want.

The software doing this is called Compiz Fusion.  The basic settings in teh appearnce dialog just loads some ubuntu presets into compiz.  If you want more control over how compiz looks then you need to isntall the compizconfig-settings-manager:

```
sudo apt-get install compizconfig-settings-manager
```

This will then appear as an exta option (custom) in the appearances dialog.  You might also want to visit [http://www.gnome-look.org/](http://www.gnome-look.org/) to get themes and ideas for how you want your comp to look.  There are usually "post your screenshots" threads around these forums too if you want more ideas.  Good luck!

Btw... Compiz was doing this a long time before windows vista appeared ;)

---

### Post by MasterCylinder on 2008-04-16
Sorry, Im a noob


Is there a problem between Compiz and my Graphics Card?

I used [qoute]sudo apt-get install compizconfig-settings-manager[/qoute] to get the package...

BUT, when I go through Appearance and try to set anything I get the following error message.

[qoute] The Composite extension is not available [/qoute] 

Is there a problem between it and my card (ATI Radeon X1600 pro)? Or am I missing something? Please help

---

### Post by Tatty on 2008-04-16
have you installed the proprietry drivers for you card?

---

### Post by joshrobinson on 2008-04-16
are you talking about this?
check the screenshot below

if this is what your looking for, its the compiz plugin called shift switcher
with the switcher mode set to flip

you will need to install compiz, your video drivers, and ccsm

---

### Post by anewguy on 2008-04-17
> **MasterCylinder said:**
> Sorry, Im a noob


Is there a problem between Compiz and my Graphics Card?

I used [qoute]sudo apt-get install compizconfig-settings-manager[/qoute] to get the package...

BUT, when I go through Appearance and try to set anything I get the following error message.

[qoute] The Composite extension is not available [/qoute] 

Is there a problem between it and my card (ATI Radeon X1600 pro)? Or am I missing something? Please help

You need to be sure you have the driver for your card installed and working, but the error message you are getting suggests to me that you may be (depends on your driver) missing a section of your /etc/X11/xorg.conf  file (to edit this you need to use sudo)  as shown below:

Section "Extensions"
        Option "Composite" "Enable"
EndSection

:)

---

### Post by Spoken on 2008-04-17
its a plugin your wanting.  search compiz plugins on this forum.

---

