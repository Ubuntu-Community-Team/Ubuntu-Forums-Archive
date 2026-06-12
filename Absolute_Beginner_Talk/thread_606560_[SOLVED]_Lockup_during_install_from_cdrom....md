---
title: "[SOLVED] Lockup during install from cdrom..."
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by dacium on 2007-11-08
Hi, my PC is hanging during install. I have tried both gusty and the other one that starts with f.
 I have tried by run/install option and the admin install option. all 4 times the process starts and there is CDROM activity, but after about 2 minutes, no more CDROM nor HDD activity and system just sits there with nothing on the screen at all.

My specs are:
athlon 2000+
256MB 266ram
120GB HDD
S3 4MB PCI Video card

Thanks for any help.

---

### Post by P4man on 2007-11-08
A 4Mb VGA card ?  Im guessing it has something to do with that.. maybe X is trying to use a too high resolution? or something not supported by your monitor? You could try two things:
-press control + alt + F1 when the pc seems "stuck". If this gives you a terminal, then the problem is most likely related to graphics configuration.
- select a resolution in the cd boot menu (F2 or F4 or something I think). try 800x600

Also make sure to run the "test CD for errors" option. Chances of having 2 bad discs may seems slim, but maybe your drive is the cause..

---

### Post by dacium on 2007-11-08
Thanks for your help. I replaced CD-ROM, now I seem to progress further, but now I get the monitor going out of range/sync.
I press control+alt+f1 and after a few seconds the screen comes back in sync, but it is only a completely blank screen, no cursor or terminal.
I'll try to change that resolution in the boot menu must have missed that!

---

### Post by P4man on 2007-11-08
LOL, read my post above. We posted simultaneously, but it looks like I guessed right twice :)

---

### Post by dacium on 2007-11-08
I can't seem to find anything about changing resolution.

In the boot menu it has F4 VGA. When I press F4 a little box pops up saying VGA. 
There is an option for safe graphics mode, but the same thing happens.. :( Looks like I need to get another card graphics card i guess.

---

### Post by dacium on 2007-11-08
wait... I have replaced the monitor :D and now I can load up in 640x480, seems the monitor does not support 640x480 but the video card won't work above 640x480 :D. Would you believe I also had a bad RAM stick and bad caps in the power supply! Finally I got it working! Thanks for your help :D

---

### Post by P4man on 2007-11-08
When you press F4, you are not getting a list of different resolutions to choose from ?

---

### Post by dacium on 2007-11-08
if you don't mind helping a noob... where do i got once at the desktop to try and test a change of resolution/color depth?
And yeah when I pressed F4 the only option I got was "VGA" ... which is weird. I tried it on my laptop and got options for different resolutions. Maybe its because the video card is really old?

---

### Post by P4man on 2007-11-08
640x480 is unbearable. Im not even sure you can access all the dialogs in that resolution.
time to consider replacing your machine I would say :)

Don't forget to mark this  thread as "solved" (in thread tools, top right)

---

### Post by P4man on 2007-11-08
to change resolution, go to system > preferences > screen resolution.
But if you couldn't change it in the boot menu, I doubt you will be able to change it now.
Let me check if your videocard is supported..

---

### Post by dacium on 2007-11-08
Yes my only option is 640x480 Hz nothing else comes up in the drop down menus.

Oh well I was expecting to have to buy another video card anyway. I was hoping to use this system as a PVR, just got to add a TV tuner and a fx5200 with TV out. Ive got AGP on the motherboard so I shouldn't have any problems, thanks for your help. I just wanted to make sure the system could run before I forked out the cash for the video cards :) Think ill get some ram while im at it too...

---

### Post by P4man on 2007-11-08
A PVR.. oh dear, your problems have not even began then. I have tried several times turning one of my boxes into a Linux HTPC, but have given up and reverted to XP Media Center. Best of luck in your attempt, you are going to need it!

You might try this:
[http://linuxmce.com/](http://linuxmce.com/)

No need to install ubuntu, its a self contained system (installs Kubuntu + all the rest). If it works for you then, GREAT, but it didn't work for me :(

---

### Post by dacium on 2007-11-08
I've done a lot of checking around and made sure I am buying a video card and tuner card and using the linux that people have got it working on, I hope. I can always revert to windows though if I must... :(

---

