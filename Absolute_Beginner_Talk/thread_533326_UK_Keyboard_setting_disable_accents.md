---
title: "UK Keyboard setting disable accents"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by streetsurfer on 2007-08-23
Most of the threads seem to be on how to add accent input but i would like to disable it
I set it to UK english and when i type " " or ~ ~ icons they accent the letters instead. I want to disable that. is there anyway to do so?

Thanks.

---

### Post by expatCM on 2007-08-24
This sounds a bit strange ......  I wonder, if you have a look at System / Keyboard Preferences / Layout, what is the layout you have selected?

---

### Post by streetsurfer on 2007-08-24
Generic 101-key PC

United Kingdom International (With dead keys)

I figured since its UK Keyboard it shouldn't have this issue

for example if i want to type we're
i would have to type

we'<space>re

to get the apostrophe otherwise i get we&#341;e (accented r)

---

### Post by expatCM on 2007-08-25
I do not understand why you are having this problem ......   are you by any chance able to test using  another keyboard, preferably a PS2 interface?

---

### Post by streetsurfer on 2007-08-25
nope :(
one and only keyboard.
im using a wired Microsoft Digital Media Keyboard 1.0A (list only had the wireless version)

I set the settings to US English and there are no accent problems but that means 1/2 my keys are in the wrong places >.<

---

### Post by fcumok on 2007-09-24
Did you find a solution to this as I'm having the same problem with my Toshiba laptop.

Everything was fine until yesterday when it seemed to switch itself to US settings. It seems as though the only options that I have under system/preferences/keyboard are Dvorak, International (with Dead Keys) or Macintosh. The only one that has the correct key setting is the International one but then I have to use spaces to get rid of the accents it wants to put on. I think it would work if I didn't have dead keys on but there isn't that option.

Interestingly although it says U.S. English in here when I look at my xorg.conf file it reports that it's a GB layout as shown below:

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Any help would be much appreciated! :)

---

### Post by fcumok on 2007-09-25
bttt

---

### Post by fcumok on 2007-09-26
Right i've looked into it a bit more and found that on another Ubuntu machine I have an extra UK keyboard setting, it appears that this is the one I need. Is there a way I could add this keyboard setting back into my ubuntu on the laptop without a reinstall?

---

### Post by fcumok on 2007-09-29
I've done a reinstall and all was fine until I installed compiz fusion. Any ideas why this should cause a problem?

---

### Post by fcumok on 2007-09-29
bump

---

### Post by tek1024 on 2007-11-18
The secret is the "deadkeys" setting.  That makes a standard keyboard (US or UK EN) go nuts.

I'm running Xubuntu (Xfce4) and I thought I'd be clever and enable deadkeys on my new dual-boot install, but it's been nothing but a pain (I forgot the difference between using "compose characters" for international characters and a literal deadkey setting).  I want to be able to use proper Deutsch, but I don't need any help from an overzealous layout making all my double-quotes into umlauts!

I *think* using "XkbModel" set to "pc105" in your /etc/X11/xorg.conf file turns on deadkeys by default, even if you don't have the "_intl" designation in your "XkbLayout".

Try this (this is a generic UK-standard 104-key setup, going by your usage of "gb" as the layout designation--I'm using the US setting):

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "gb"
EndSection
```

You may need to reboot (or at least kill/reload X-windows) for these changes to take effect.  There may be other caveats and sub-settings that your window manager is dinking with; in Xfce4, this works AFAIK.  If you're using GNOME, you can. I think, use gnome-keyboard-properties to set this without going to the .conf file.

HTH!

---

