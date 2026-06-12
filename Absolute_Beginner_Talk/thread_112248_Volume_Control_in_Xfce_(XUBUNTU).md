---
title: "Volume Control in Xfce (XUBUNTU)"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by AWAL on 2006-01-03
I am using Xfce with the volume mixer plugin in the panel.  I can't seem to get the mixer to increase the volume level.  It always returns to 0%.  So far, sound works fine when playing a game.

Anyone using xfce have an answer?  Is it my permissions I need to change?

Hope someone can help.

---

### Post by Stinger on 2006-02-01
Right click the volume control and select properties , in the properties window you have to select mixer **device** usually /dev/mixer unless you have more soundcards.
Next you have to pick your **Wannabe Master** from the drop down menu , close the properties window and hopefully it works now.

In the Xfce Settings Manager , sound section you can select which controls you want visible in your mixer.
:-D

---

### Post by sml on 2006-05-06
Thanks Stinger. Awesome.

---

### Post by tommie74 on 2007-04-08
For beginners like myself looking here to find an answer of how to get a sound volume control in Xubuntu: right click the panel (the bar where the applications menu is, part of the Xubuntu desktop) and the click Add New Item. A window will pop up where you can select volume control from the available items. Now you will have a little button on the panel where you can easily adjust the sound volume. Clicking the right side of the button will change the volume, the left side will open a more sophisticated, for me useless volume control window.

---

### Post by r00tintheb0x on 2007-04-08
Try text based aumix

---

### Post by wilberfan on 2007-05-24
> **tommie74 said:**
> For beginners like myself looking here to find an answer of how to get a sound volume control in Xubuntu: right click the panel (the bar where the applications menu is, part of the Xubuntu desktop) and the click Add New Item. A window will pop up where you can select volume control from the available items. Now you will have a little button on the panel where you can easily adjust the sound volume. Clicking the right side of the button will change the volume, the left side will open a more sophisticated, for me useless volume control window.

I can't get this to work on either of my Feisty machines!

I'm running 2 different Feisty boxes--one on my Pentium 4 (32-bit) the other on my AMD64x2 (64-bit).

I've been unable to get a volume control icon to appear on ANY panel on *either* machine!   I've right-clicked on the panel, selected "Add New Item" and selected "volume control"...

I see a a black line appear for a second at the right side of the panel--but then there is no icon.   I can run xfce4-mixer in a terminal to adjust the volume--but that's kind of a pain in the ***.

(On a related matter, is it possible to create a keyboard shortcut in xfce to raise or lower the volume?  This is by far my favorite method to control volume levels!)

---

### Post by Echow on 2007-06-02
That is very strange.....Are you able to listen to music etc?
I would also like to find out the keyboard shortcut to increase/decrease volume...
Ed

---

### Post by wilberfan on 2007-06-02
> **Echow said:**
> That is very strange.....Are you able to listen to music etc?

I HAVE audio--but if I want to change the levels, I have to do a xfce4-mixer in a command line to change it...

---

### Post by Echow on 2007-06-04
Hrmm this seems to happen when I already have a volume control button in the panel......theres no chance that you already have one do you? It shuold look like a small whistle with a little green (at least mine is green) bar next to it.
Try adding it to a different panel and see what happens.
Ed

---

### Post by mydrac on 2007-06-05
maybe you must try to add other item and see what happend propably isn't just the volume control maybe are all item and the problem could be the configuration of the panel or other like that.

(Sorry for my english)

---

### Post by Echow on 2007-06-06
BTW! I found something:
[http://alvonsius.wordpress.com/2007/01/08/xfce-volume-controlling-with-keyboard/](http://alvonsius.wordpress.com/2007/01/08/xfce-volume-controlling-with-keyboard/)
If you use amixer you can make a keyboard shortcut control volume. Neat. Hope this helps
Ed

---

### Post by jis on 2008-03-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/xfce4-mixer/+bug/90261](https://bugs.launchpad.net/xfce4-mixer/+bug/90261) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				amixer works better than aumix for me. If I run aumix in terminal it just displays  "aumix:  SOUND_MIXER_READ_DEVMASK" and does nothing useful. But even amixer is not perfect. It has to start the program again and again for each change. Pressing key long time will change level only one step. It would be better if the panel item could handle the shortcuts. It should handle muting/unmuting as well, although this is minor problem. For many the panel plugin does not work at all, see the link!

---

