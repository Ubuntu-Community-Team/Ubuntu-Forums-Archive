---
title: "Stuck @ 800 x 600 res.- messed up X11 file?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by 3wells on 2008-02-16
Really new to this - so, please bare with me. I tried the search and got too much info!

Began only 2 days ago, been a dos/windoze user since the '80's... A lot of good that does...

Couldn't get my multi button mouse to work... edited... mouse still doesn't work... didn't touch the display or adapter section, rebooted, Stuck at 800 x600 res? (backed up my xorg,
I now have about 4 'failsafe' copies. I presume they're like registry backups?

Ubuntu 7.1 Gutsy, 
Tweak 0.2 installed
Wine installed

Here's my config >>>

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc 3D Rage Pro AGP 1X/2X"
	Monitor		"BenQ FP737s-"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1112x834" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

I've tried to reinstall the correct driver, a generic is installed now, each time I try to change it and reboot, stuck?

BTW - Is there a restore function?

Please help!

3

---

### Post by PurposeOfReason on 2008-02-16
What did you call the backup files you made?

---

### Post by 3wells on 2008-02-16
> **PurposeOfReason said:**
> What did you call the backup files you made?
/etc/X11/xorg.conf.failsafe, /etc/X11/xorg.conf.failsafe.1, /etc/X11/xorg.conf.failsafe.2 etc, etc...

3

---

### Post by PurposeOfReason on 2008-02-16
In a terminal run:

sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

to replace the file with your backup.

---

### Post by 3wells on 2008-02-16
Okay, that didn't work. I wasn't asked for a choice of backups? Rebooted...

Gawd, U is fast! Would relly like to get it back! Don't want to start over! Still getting used to the interface, I found what looked like a device manager yesterday, can't find it today?

Can I update the driver from there?

3

---

### Post by GreenfieldMark on 2008-02-16
I don't suppose you tried messing with the screen resolution preferences? Just under System -> preferences -> screen resolution. There's also a button for mouse preferences. 

I may sound like an idiot stating the obvious, but new Ubuntu users might miss those.

---

### Post by PurposeOfReason on 2008-02-16
You could if you can find it. If you can get a terminal I believe it is called "restricted-driver-manager" Just start typing and press tab every now and then and it'll try to complete it for you.

---

### Post by Ivorydawn on 2008-02-16
Hi,

Can you boot using the recovery option from the Grub screen then try reconfiguring the Xserver using sudo dpkg-reconfigure xserver-xorg -phigh

Regards

Andrew

---

### Post by 3wells on 2008-02-16
Okay, all you good folks! Done!!!!** It's back!** 

Sadly, I tried a couple of things before hard rebooting - hence, I don't know which suggestion worked (idiot!)

A couple of posts back, someone asked if I tried the obvious - yup, I did.

** However, I now have something that resembles a small 'bar code' box on the upper left  corner of the screen? What's that about??

Off topic - where's the 'device manager'? Can I update a driver from there, like you can with the other guys?

Thanks again!

3

---

