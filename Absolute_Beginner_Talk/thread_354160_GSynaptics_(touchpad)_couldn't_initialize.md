---
title: "GSynaptics (touchpad) couldn't initialize"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by euphemism on 2007-02-05
I tried to use the touchpad app that comes from the GSynaptics package, but got this error:

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

I used the locate command for xorg.conf but the only file i could find was something like xorg-server.conf, and doing a quick search through the text file there was no "SHMConfig" value to change.

Anyone have a workaround for this?

---

### Post by NewOldTimer on 2007-02-05
Hi, I'm new here but I'll offer this up and I'm sure if I'm wrong one of these guru's will straighten us up.
 sudo  gedit  /etc/X11/xorg.conf           when I was trying to disable my touchpad I had to add the line "SHMConfig" under input device's. Don't know for sure with your case, but at least you can have a go see look while waiting for more informed answers.

sorry don't know how to put code/command in the way they all do for copy/paste

---

### Post by euphemism on 2007-02-05
Just tried that, but my xorg.conf file is empty.

Thanks though, anyone else have this problem before?

---

### Post by shareMenaPeace on 2007-02-05
> **euphemism said:**
> Just tried that, but my xorg.conf file is empty.

Thanks though, anyone else have this problem before?
Make sure to type "case sensitive"

```
gedit /etc/X11/xorg.conf
```

---

### Post by Zaen on 2007-02-05
I don't know if it is possible for that file to be empty (correct me if I'm wrong). even if it is, check for mistakes when typing in a command
example: 
```
nano /boot/grub/menu.list
```
versus:
```
nano /boot/grub/menu.lst
```
depending what text editor you are using, it could make a world of a difference.
hope this helps

---

### Post by marx2k on 2007-02-05
copy/paste either:

'sudo nano /etc/X11/xorg.conf'

'gksudo gedit /etc/X11/xorg.conf'

I suggest the second option since it's GUI based... you have to know how to use nano in console/terminal if you go with the first one.  I would suggest learning that, though, since as a linux user you will be editing a LOT of files by hand and its faster/easier (after a while) in terminal anyway

---

### Post by euphemism on 2007-02-05
You guys are right, I must've typed something wrong because I just copied/pasted and it came up.  However, I have a ton of "input device" sections.

I added the line to one of them, that I thought looked most-correct, like this:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	**Option		"SHMConfig"		"true"**
EndSection
```

But it didn't work.  x_X  Still getting the same error message.

Talk about jumping straight into the deep-end before you can swim. :)

Thanks for the tips so far!

---

### Post by NewOldTimer on 2007-02-06
I've been in the deep end so long, I'm growing gill's. did you save your edit and restart X, Remember as I said earlier I'm real new at this but I just can't stand by and watch you splash around. If you ask these pro's in more detail they will throw you a line. Wish I could help more but in my case... less IS more.

---

### Post by euphemism on 2007-02-06
Yep I saved/restarted, thanks for the encouragement!

I just tried QSynaptics and got this error when I tried to run it:

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
users home is /home/[edited]
Can't access shared memory area. SHMConfig disabled?

```

Then the QSynaptics window pops up but all of the options are grayed out.

None of the devices in the config file I edited earlier had any "168" value (did a ctrl+f on the doc for it)

Hope that helps someone help me! :D

---

### Post by NewOldTimer on 2007-02-06
When your qsynaptics window opened was there a "detected information" section? if so maybe that will be the key to your worrie's.

---

### Post by euphemism on 2007-02-06
I installed some driver that I found in the package menu, rebooted, and now both qsynaptics and gsynaptics are working fine.

Neither of them seem to work with my Toshiba Satellite's touchpad though.

Oh well =(

Thanks anyways, though. :)

---

### Post by NewOldTimer on 2007-02-06
only other thing I can offer is this  

[http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/)

---

### Post by euphemism on 2007-02-06
Simply changing that SHM value from "true" to "on" worked perfectly! (Incase anyone else has my same problem.)

Circular scrolling/tapping working perfectly now :D

Thanks!

---

