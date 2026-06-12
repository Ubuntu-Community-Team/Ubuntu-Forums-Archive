---
title: "I messed up xorg.conf"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by Ryan H on 2006-06-10
I tried to fix my resolution but in the proccess corrupted the rest of the configuration file. It made a back up but I can't remember where it says it was. I'm in ubuntu on text only mode and I'm guessing if I new the location of the backup I could copy it to the location of the corrupted file and overwrite it. Can anyone help me with this?

-Ryan H

---

### Post by tonyr on 2006-06-10
**/etc/X11/xorg.conf.<date-spec>**

My last one was **xorg.conf.20060608171305**.

Remember to use **sudo cp**.

---

### Post by _simon_ on 2006-06-10
the backup should be in /etc/X11/

from terminal just do

cd /etc/X11
ls

Your original is obviously xorg.conf

anything else with xorg.conf in is a backup, I seem to have 6 backups lol

---

### Post by Ryan H on 2006-06-10
Thanks! I just couldn't remember where that was. I just moved the backup and overwrit the original and it was all good.
Thank you so much!

-Ryan H

Edit: Well everytime I try to change the file in terminal I allways mess it up. Is there a way I can just edit the resolution, or manualy edit the file for just resolution?
I found out how I could edit it, but how do I change the permissions of a file in the terminal?

-Ryan H

Edit: I changed the file permissions and edited it so it read:
"
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
"
And I rebooted everything works but I still can't change my resolution to 1280x1024, it's not on the list.

-Ryan

---

### Post by Ryan H on 2006-06-10
Sorry I didn't mean to dubble post.

---

### Post by tonyr on 2006-06-10
Read [this]("https://wiki.ubuntu.com/FixVideoResolutionHowto") for som eclues.  (It was originally written for **Hoary**,
but has been updated). You'll need to know the 
veritical sync and horizontal refresh rates for your monitor.  The file
**/var/log/Xorg.0.log**  might have some indication of what's going wrong when
X starts.

---

### Post by nalmeth on 2006-06-10
you can run

sudo dpkg-reconfigure xserver-xorg

for a wizard type configuration

you'll probably have to restart X for changes to take effect.

---

### Post by richbarna on 2006-06-10
You can also manually scroll through the xserver screen sizes by clicking :-> Ctrl-Alt with either + or -

---

### Post by Ryan H on 2006-06-10
The Ctrl+Alt + thing worked! Not I have my resolution set up perfectly! Thank you for all your help guys; now I can fully enjoy Ubuntu. :) 

-Ryan

---

