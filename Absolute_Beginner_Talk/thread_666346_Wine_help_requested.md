---
title: "Wine help requested"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by newbeeman on 2008-01-13
Installed wine for Ubuntu from Synaptic, works fine. I then installed DVD shrink, which also works fine apart from not finding my DVD drive, that works well in Ubuntu, reading and writing.
I am obviously missing something, but as a newbie to Linux have no idea where to start. Advice requested.

---

### Post by Malta paul on 2008-01-13
Wine will normally use /E for your drive. If this doesn't work you can configure using 'Configure wine'
Check this out:
[http://www.winehq.org/site/documentation](http://www.winehq.org/site/documentation)
Have fun :)

---

### Post by ckuka on 2008-01-13
Are you able to use other windows applications using wine? If not it may be wine. I personally have found it very difficult to use wine though sometimes it is needed. 
Have you tried using K9Copy- this is an open source alternative


Type this into a terminal, or search for the package in the package manager


sudo apt-get install k9copy

good luck!

---

### Post by newbeeman on 2008-01-13
> **Malta paul said:**
> Wine will normally use /E for your drive. If this doesn't work you can configure using 'Configure wine'
Check this out:
[http://www.winehq.org/site/documentation](http://www.winehq.org/site/documentation)
Have fun :)

I have read, reread those pages. The very first thing I tried gave me an error. I believe those pages are earlier than the Ubuntu issue.
I did try Configure wine, but it is double dutch to me.
Can you help further?

---

### Post by newbeeman on 2008-01-13
> **ckuka said:**
> Are you able to use other windows applications using wine? If not it may be wine. I personally have found it very difficult to use wine though sometimes it is needed. 
Have you tried using K9Copy- this is an open source alternative
Type this into a terminal, or search for the package in the package manager
sudo apt-get install k9copy
good luck!

I have spent a great deal of time with K9copy, K3b plus a host more but cannot 'get it right' so thought I would try the old staples. DVD shrink and Image burn. Have got Shrink working, now I just need 'Image'.
That works in 'Build' mode, but it doesn't 'see' the DVD drive. There is a switch "Search for SCSI/ATAPI devices" all that gives is 'No Devices'.
Any ideas?

---

### Post by fiddledd on 2008-01-13
The only app that worked for me in wine and saw my DVD Drive was Tmpgenc DVD Author. If you can get DVDShrink to just save to a folder (VIDEO_TS and AUDIO_TS) which I would think it did anyway, you can use K3B to burn the folder to DVD. I have used K3B to burn the DVD and it played fine on a standalone player. Not used K3B for a while but it has a DVD option so it burns the correct filesystem etc.

---

### Post by brett611 on 2008-01-13
I had the same problem with DVDShrink.  Here's the "partial" solution.  See attached screenshot
Winecfg
Drives
Select the cdrom and change the "type" to cd-rom from the default of hard drive/local disk.

This allows dvdshrink to see your drive.  

Now...I'm trying to -backup- my Simpsons movie dvd and it tells me the drive is not ready.  It works on my window XP laptop so there's some other piece I'm missing.

One step closer anyways.

---

### Post by Danyl on 2008-01-17
I found this guide particularly useful (even though it was written by a Fedora user and not specifically for Ubuntu).

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Tutorial_Setting_up_DVDShrink_thru_Wine_on_Fedora_or_other_RPM_based_distros]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Tutorial_Setting_up_DVDShrink_thru_Wine_on_Fedora_or_other_RPM_based_distros")

I followed it and everything works great except when DVD shrink finishes analyzing the DVD, it pops up with an error message saying:

"Dvd shrink encountered an error and cannot continue failed to read file "d:\".
Not ready".

Not sure how to fix it from here.

---

### Post by Danyl on 2008-01-17
> **Danyl said:**
> I found this guide particularly useful (even though it was written by a Fedora user and not specifically for Ubuntu).

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Tutorial_Setting_up_DVDShrink_thru_Wine_on_Fedora_or_other_RPM_based_distros]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Tutorial_Setting_up_DVDShrink_thru_Wine_on_Fedora_or_other_RPM_based_distros")

I followed it and everything works great except when DVD shrink finishes analyzing the DVD, it pops up with an error message saying:

"Dvd shrink encountered an error and cannot continue failed to read file "d:\".
Not ready".

Not sure how to fix it from here.

Weird. I got it working somewhat....It started to decrypt and then the same error message.

---

