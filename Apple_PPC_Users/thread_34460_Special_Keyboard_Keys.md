---
title: "Special Keyboard Keys"
date: 2005-05-15
forum: Apple PPC Users
---

### Post by ipixel on 2005-05-15
BEGINNER'S QUESTION:
Is there a way in Kubuntu to make some of the 'special keys' in the apple keyboard - volume up/down/mute and disk eject - work? 

Any suggestions welcome!

---

### Post by johj on 2005-05-15
I don't know about kubuntu, but on my powerbook5,6 pbbuttons does the job. See [http://pbbuttons.sourceforge.net/](http://pbbuttons.sourceforge.net/)

---

### Post by ipixel on 2005-05-16
Thanks for the tip!

Is this a program that we have to install optionally, or does it come standard with the Kubuntu installation? If so, do we control it somewhere in the 'Control Panel', or do we have to use the command line?

Many thanks!

---

### Post by ipixel on 2005-05-18
UPDATE:

It seems like this program is already pre-installed - it is listed during the startup sequence, before the window manager comes on. However, the keys do not work - for instance, the 'Eject' key does not eject the CD. 

Where do we configure it? Is there a GUI, or do we have to use the command line?

---

### Post by ipixel on 2005-05-21
Could someone post instructions on how to configure the following keys, so that they work as expected with a Mac keyboard?

1) Which keyboard layout do we select, for an Apple USB Extended Keyboard?

2) How do we configure the SOUND UP/DOWN and MUTE buttons?

3) How do we configure the EJECT button?

Many thanks in advance for any help!

---

### Post by maximum on 2005-05-22
[QUOTE=ipixel]Could someone post instructions on how to configure the following keys, so that they work as expected with a Mac keyboard?

1) Which keyboard layout do we select, for an Apple USB Extended Keyboard?
[/QUOTE]

well, i don't know witch layout you need. 
I'm using a spanish tibook keyboard, but no one X11 layout is correct for apple keyboards so i have used xmodmap to create mine.
You can found my layout (in italian language) here:
[http://www.maximumdebian.org/modules.php?op=modload&name=News&file=article&sid=358](http://www.maximumdebian.org/modules.php?op=modload&name=News&file=article&sid=358)

[QUOTE=ipixel]
2) How do we configure the SOUND UP/DOWN and MUTE buttons?
3) How do we configure the EJECT button?
[/QUOTE]

open the menu System/Preferences/KeyboardShortCut
Here you can configure your 4 keys as you need.

best
MaX

---

### Post by open_flax on 2005-05-23
Hello
  if you use GNOME you can make some shortkeys. you see a menu preference and shortkeys. 
I have a ibook G4 and i use this option.
baybay

---

### Post by karl_kashofer on 2005-05-23
Hi !

Go to System, Administration, Synaptics.
Enable the Universe repository
Install "powerprefs"

Then go to Applications, "Run Applications", type powerprefs

Configure your buttons with "teach in"

pbbuttons is installed by default, but this small gui makes configuring it so much easier.

BTW: by default middle and right mouse button are mapped to F11 and F12. If that interferes with your setup or you want them somewhere else edit /etc/sysctl.conf
(tip: get the keycodes from powerprefs "teach in")

Cheers,
Karl

---

### Post by cow_racer on 2005-06-03
[QUOTE=ipixel]UPDATE:

It seems like this program is already pre-installed - it is listed during the startup sequence, before the window manager comes on. However, the keys do not work - for instance, the 'Eject' key does not eject the CD. 

Where do we configure it? Is there a GUI, or do we have to use the command line?[/QUOTE]

I had warty and now have switched to hoary.  I found that the eject key, the volume keys, the brightness keys no longer work.  Then I tried holding the "fn" keys then press the eject keys and the cd ejects.  But if I do not hold the "fn" keys, press the eject key gets me menu that I would get by doing a right mouse click.  I guess this must have been the default setting.  I actually like it better this way.  :)

---

### Post by gtomorrow on 2005-06-24
i too am having problems with the volume/eject keys on  my apple pro keyboard. powerprefs may work but only on powerbooks. i even tried xev to find the keycodes to modify my .xmodmap but xev returns NOTHING! they are dead keys as far as hoary is concerned. did somebody say "bug?"

---

### Post by ipixel on 2005-06-25
To say that I am very disappointed with Ubuntu/Kubuntu would be just mildly understating it...

Keyboard support is absolutely APPALLING! Apart from the problems with these alternate keys, there is no instruction anywhere (in either Gnome or KDE) for how to select and type international characters (such as accented latin letters).

It's back to OS X for me, until Ubuntu is truly ready for international use, and has some of the basics (like keyboard) worked out...

Keep up the good work.

---

