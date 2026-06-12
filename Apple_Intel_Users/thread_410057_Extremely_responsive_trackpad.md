---
title: "Extremely responsive trackpad"
date: 2007-04-15
forum: Apple Intel Users
---

### Post by Seamyst on 2007-04-15
I installed Feisty on a partitioned MacBook Core Duo laptop and everything else is either working fine or easily fixed.  I have one lingering problem, however - the trackpad is EXTREMELY responsive, much more so than on the Mac side.

Simply moving the cursor around is no problem, and I don't expect the two-finger scrolling feature to work in Ubuntu.  (Someone please help me on that if I'm wrong!)  It responds to a double-tap as an actual click, which doesn't happen on the Mac side.  This means that whenever I type I have to be VERY careful with my thumbs and palms not to touch the trackpad at all, or else the cursor moves and I type over something, or a bunch of text is erased, or other such fun stuff.

Is there any way to reduce or "eliminate" this problem, outside of getting a USB mouse?  Experimenting with the mouse settings in System > Preferences doesn't help.

---

### Post by martinw89 on 2007-04-15
I don't know if this will work on Macs but you can get the program "gsynaptics".  It provides a front end to adjusting settings for your touchpad.

---

### Post by bsantos on 2007-04-16
> **martinw89 said:**
> I don't know if this will work on Macs but you can get the program "gsynaptics".  It provides a front end to adjusting settings for your touchpad.


AFAIK it works on Macs, but as using synclient you have to have 

Option "SHMConfig" "on"

on your xorg.conf.

:)

---

### Post by Seamyst on 2007-04-16
Okay, now I'm a complete and total Linux newbie, and I have no idea how to get into or edit xorg.conf, or where to find gsynaptics... I used Synaptic Package Manager to download and presumably install gsynaptics, but it's not in Applications and I have no idea where to look for it otherwise.  :confused: 

I have no problems with following explicit step-by-step directions, and I can do terminal commands or anything, as long as you tell me exactly what to do.

---

### Post by bsantos on 2007-04-16
For gsynaptics you have to enable the universe repository:

System -> Administration -> Software Sources

Add a tick to 'Community-maintained Open Source software'

Then it should be available if you search on synaptic.

---

### Post by buschi on 2007-04-16
> **Seamyst said:**
> ... I don't expect the two-finger scrolling feature to work in Ubuntu.  (Someone please help me on that if I'm wrong!)  ....

also that should be possible with synaptics. it also brings along a feature that switches off the trackpad for a given time after a keystroke.

you can find more information in this forum, for example in "ubuntu feisty fawn herd 5 on my macbook", post #3 or on [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) and [http://www.die.net/doc/linux/man/man5/synaptics.5.html](http://www.die.net/doc/linux/man/man5/synaptics.5.html) .

good luck,
sebastian.

edit:
mouseemu can also switch off the trackpad after a key event, see for example [http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453) .

---

### Post by ry4nolson on 2007-04-16
go to System > Preferences > Sessions

and on the startup programs click new

add this command and name it whatever
```

syndaemon -i 0.5 -d -t -k
```

this will disable the touchpad for a half a second after you press a key unless its a modifier key (ctrl, shift, etc)

also run that command in the terminal to make it do it without having to restart.

---

### Post by Steve Shickles on 2007-04-16
Great information. Thanks

**- Steve Shickles**

---

### Post by ronocdh on 2007-04-17
Informative thread. Now seems as good a time as any to mention my issue with the trackpad (C2D MBP 15"). I was recommend qsynaptics over gsynaptics, so I installed it from the terminal, but when I run the program almost all options are greyed out, and there's a message saying "Please install qsynaptics driver!" I had assumed this would come with the package, but evidently not.

The logical apt-gets I concocted didn't help. Can anyone point me to the right command? Anyone comment on the difference between G and Q synaptics?

---

### Post by ry4nolson on 2007-04-17
i tried both i liked Gsynaptics better than Q. this is what i followed to get mine to work: [http://simon.vanderlinden.eu.org/howtos/macbook-emulate-a-synaptics-touchpad-with-ubuntu-gnulinux/](http://simon.vanderlinden.eu.org/howtos/macbook-emulate-a-synaptics-touchpad-with-ubuntu-gnulinux/)

---

### Post by Seamyst on 2007-04-17
Yes!  That did it!  Now I can brush my thumbs over the touchpad at will while I'm typing, and nothing worse will happen than the pointer moving.

Took me forever to figure out how to edit the xorg.conf file (I learned about root in the process), but I got it working.  And apparently, using the synaptics means that scrolling is now done with one finger on the right (or bottom) side of the pad, instead of two fingers wherever.

Thank you!  :D

---

### Post by martinw89 on 2007-04-18
That's cool to see you got it working, I didn't know if any of the synclient frontends would work or not for Macs (didn't know if they used the same touchpad driver).  I like qsynaptics over gsynaptics. But, gsynaptics has options for sensitivity (which is nice).  Maybe the two projects can merge sometime in the future or someone will be nice and merge the code themselves into a new project.

---

### Post by viciouslime on 2007-04-18
> **Seamyst said:**
> Yes!  That did it!  Now I can brush my thumbs over the touchpad at will while I'm typing, and nothing worse will happen than the pointer moving.

Took me forever to figure out how to edit the xorg.conf file (I learned about root in the process), but I got it working.  And apparently, using the synaptics means that scrolling is now done with one finger on the right (or bottom) side of the pad, instead of two fingers wherever.

Thank you!  :D

You can use two fingers where ever if you want to. Just add:

	Option		"VertTwoFingerScroll"	"true"

To your xorg.conf. You can also do a two finger tap for right click by adding:

	Option		"TapButton3"		"2"

---

### Post by Grafster on 2007-05-15
Brilliant! Got an old Acer Travelmate 230 to work with this method.
(the two finger scroll option doesn't work unfortunately but it's still brilliant)

This thread and the one linked to it should be wikied or sticked or something.

---

