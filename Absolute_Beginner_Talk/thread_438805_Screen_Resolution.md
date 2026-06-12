---
title: "Screen Resolution"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by BarryW on 2007-05-10
I have just installed Ubuntu on an ibm thinkpad x40 laptop which has an external monitor attached. The install was fine and I am generally very pleased with it. the only issue I have is the maximum resolution on the external screen I can get is 1024*768. 

Does anyone know of any way to increase this. I have an

85852/855GM integrated Graphics card

Many thanks

Barry

---

### Post by LaRoza on 2007-05-10
Try this first, it fixed mine:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

Next step would be to edit your xorg.conf file. This is not difficult, however, you should back it up with:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Next, you'll need to edit it, it is filled with a lot of information but look for the something like this:
[quote]
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [GeForce 6150 LE]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
[/code]
It is about halfway down and has many subsections.

Now put your screens optimal resolution first in the list in every subsection, "1280x1024" was not there by itself, I put it there.

Save, exit, reboot

---

### Post by BarryW on 2007-05-10
Hmm,

1st one appeared to do nothing, 2nd one caused my machine to give me a blank screen !

I booted in recovery mode, checked I had made the mod correctly to xorg.conf (I had) so copied the old one back and it now works again ok albeit at the lower resolution still

Any other thoughts welcome

Regards

Barry

---

### Post by Kobalt on 2007-05-10
Are you sure you made the first step properly ? Try it this way :
Open up the Terminal and enter ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available **by hitting the spacebar** then validate with Enter. Finally, press Ctrl+Alt+Backspace to **restart X**, and here you go.

---

### Post by BarryW on 2007-05-10
Very many thanks for your help, this worked fine at one of the resolutions I tried

Regards

Barry:) :) :)

---

### Post by Kobalt on 2007-05-10
You're welcome :)

---

