---
title: "no sound in vmware"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-11-19
I am not getting sound in vmware... I have installed all files in synaptic that have alsa in them and here is my soundcore...

jon@office:/usr/src/alsa$ modinfo soundcore
filename:       /lib/modules/2.6.15-27-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
depends:
srcversion:     DD426F1CCA2CC5F060F6F92
jon@office:/usr/src/alsa$

I use Dapper and run WinXP Home in a virtual machine. Everything is smooth but no sound at all.
Am I missing something here?

---

### Post by nickburns on 2006-11-19
I did not get sound working until I install vmware with the following steps...

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

good luck.

---

### Post by munkyeetr on 2006-11-19
Not sure if you've fixed your sound problem...

Do you have VMWare Tools installed? That may help.

---

### Post by saintj0n on 2006-11-19
Yes. I have VMWare tools and I downloaded sound card drivers but still no sound. I Tunes even says there is a sound card problem.

---

### Post by igknighted on 2006-11-19
Are you using player or server?  I know that when I make a Virtual Machine I need to manually add a sound card in the VM setup menu (I use server, I have never used player so I can't help if you are using that)

---

### Post by saintj0n on 2006-11-19
No sound yet and not sure how to delete a virtual machine that I accidentally created. I will try putting in an old SBLive! Card....

---

### Post by Atomic Dog on 2006-11-20
There is a fix on vmware's site somewhere.  I couldn't locate it but this thread tells you where to get the patch:
[http://www.vmware.com/community/thread.jspa?threadID=47101&tstart=60](http://www.vmware.com/community/thread.jspa?threadID=47101&tstart=60)

I installed per the instructions and have perfect sound now.

---

### Post by munkyeetr on 2006-11-20
Re: deleting a virtual machine you accidentally created...

In VMWare workstation, on the opening tab where you Power On your virtual machine, right-click the heading on the tab at the very top, and choose "Delete from Disk".

I have no other suggestions about your sound issue, sorry.

Good luck.

---

