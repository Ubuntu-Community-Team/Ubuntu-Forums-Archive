---
title: "unable to boot after install; please help"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by westyonfire on 2007-11-11
Hi everyone :)
this is my first post as an ubuntu user. I am a complete linux newbie so I kinda need any replies in..layman's speak.

I'm competent enough with windows so the downloading and burning of the .iso went fine. the md5 and cd integrity check confirm. The install also went fine but after the first reboot when it asks you to eject the cd the boot takes about 5 mins of blank screen then finally I see that tan coloured blank screen and a circular loading cursor. it doesn't get past this and the only thing i can do is press the power off button. 
I read and followed this thread but to no avail
[http://ubuntuforums.org/showthread.php?t=460114&highlight=cosbear](http://ubuntuforums.org/showthread.php?t=460114&highlight=cosbear)

reading on it sounds like its something to do with my radeon 9200M...can anyone help me???
any help at all would be much appreciated.

---

### Post by Supergoo on 2007-11-11
Try this reinsert your ubuntu CD and when it comes up with the menu, look for the one that say boot from Hard disk, choose that and see it will will boot into Linux for you, then shut down and restart with out the disk, this worked for me with 7.04 version...




Supergoo

---

### Post by P4man on 2007-11-11
A few questions:
1) what is the rest of your hardware specs ?
2) if you boot normally, try pressing control+alt+F8. Do you get a console display, and if so, what do the last lines say? You might try going back to the graphical environment with control+alt+F7 although that likely wont work.. yet.

---

### Post by Sef on 2007-11-11
> A few questions:
1) what is the rest of your hardware specs ?
2) if you boot normally, try pressing control+alt+F8. Do you get a console display, and if so, what do the last lines say? You might try going back to the graphical environment with control+alt+F7 although that likely wont work.. yet.

Also what version of Ubuntu are you using?

---

### Post by westyonfire on 2007-11-11
Hi thanks so much for your replies. I just tried the reboot with the ubuntu cd in and it still gave the same result.

To answer the other questions, I have a sony vaio laptop (about 4 yrs old)  running a 3gh pentium 4 with 1 gig of ram. Its dual booted with windows xp. oh and the misbehaving creature in question is the gutsy gibbon...is there anything else you need to know?
again, thanks heaps for your replies guys.

---

### Post by P4man on 2007-11-11
To quote myself:
>  2) if you boot normally, try pressing control+alt+F8. Do you get a console display, and if so, what do the last lines say? You might try going back to the graphical environment with control+alt+F7 although that likely wont work.. yet.

Also, what resolution is your LCD ? Maybe Ubuntu isnt recognizing it properly and you'll simply have to change the resolution in xorg.conf. Before I talk you through that, try the above first

---

### Post by westyonfire on 2007-11-11
also, pressing Ctr + Alt + F8 intermittantley during the boot up did nothing :(
I've been reading that a lcd screen that cant handle the refresh rate? can do something similar..but if it was that would i be able to see the tan coloured screen and the loading mouse cursor (which freezes) ?

edit: sorry p4man, i shouldve replied after doing your suggestion. will check screen res now.

---

### Post by dnns123 on 2007-11-11
The first reboot was natural, it happens every 25 boot-ups i think. It scans your harddrive and does some maintainance. I cant help you in the desktop problem though

---

### Post by westyonfire on 2007-11-11
In windows my screen resolution is 1024 x 768 pixels with 32 bit colour quality. The live cd worked when i installed it so wouldnt it be running the same screen..specs? as the live cd?

---

### Post by P4man on 2007-11-11
I should have been more clear: press control+alt+F8 (also try with F1) when you get that orange backdrop. I can't imagine nothing would happen if your system isnt frozen (which is not the case since your mouse still moves?)

---

### Post by westyonfire on 2007-11-11
Hi p4man,
when the orange screen comes up the mouse cursor is twirling in that clock type loading action and the mouse moves the cursor. but after a few seconds the twirling loading cursor freezes its...twirling motion but the mouse can still move the cursor itself. After this happens ctr alt f8 (or F1) does nothing. I rebooted again and pressed ctr alt F8 quickly before the orange screen froze and its given me a black screen with big blue writing. the last few lines it says are: * Running local boot scripts (/etc/rc.local)........[ OK ]     but its frozen there now. hope this helps...im just wondering. Could it have something to do with the fact i have windows dual booted?

---

### Post by bulldog on 2007-11-11
How about booting the recovery [second] option in your grub?

---

### Post by westyonfire on 2007-11-11
bulldog,
the 2nd option gives me a black screen with blue writing (init?). as it was scrolling down i didnt see anything that wasnt an [ OK ] on the right side of the screen. the last line of this console type screen is: * Setting up console font and keymap...   ....... [OK ]
root@nick-laptop:#_

i sure hope your a linux whiz ;)

---

### Post by bulldog on 2007-11-11
You did login providing your username and password?

Anyway type ```
dpkg-reconfigure xserver-xorg
```
This will ask you a lot of questions about your hardware.
Answer them as good as possible [what you know for sure] or leave the default.
There will be a question about your graphics and which driver to use ,choose vesa or if you have a nvidia card nv ,choose the desired resolution [space] and unselect the ones you don't want to use.
This wil re-write your xorg.conf.

---

### Post by P4man on 2007-11-11
No, it has nothing to do with dual booting.
Time to get your hand dirty :)

Boot into recovery mode. type:

```
nano -w /etc/X11/xorg.conf
```
(careful, case sensitive!)

You are now editing a configuration file for X, the graphical interface.

Scroll down and locate the "section device" where your videocard is described. What does "driver" say ? I suspect "ATI" or "radeon". Change it to "vesa". Press control+x to close, confirm saving with Y,  type "reboot" to reboot, cross your fingers :)

---

### Post by bulldog on 2007-11-11
> **P4man said:**
> No, it has nothing to do with dual booting.
Time to get your hand dirty :)

Boot into recovery mode. type:

```
nano -w /etc/X11/xorg.conf
```
(careful, case sensitive!)

You are now editing a configuration file for X, the graphical interface.

Scroll down and locate the "section device" where your videocard is described. What does "driver" say ? I suspect "ATI" or "radeon". Change it to "vesa". Press control+x to close, confirm saving with Y,  type "reboot" to reboot, cross your fingers :)

You shouldn't do this whitout making a backup copy first.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by westyonfire on 2007-11-11
actually its not asking me for a password. it just goes straight to root. anyway im about to follow both of your..rather daunting suggestions. here goes. will be right back with answers.

---

### Post by P4man on 2007-11-11
Fair point, I agree its good practice to backup such files, but in this case Im not sure it was worth bothering with. . Its not like he is going to ever restore that xorg.conf as his current xorg.conf is non functional anyway, and changing the driver to vesa is extremely unlikely to cause additional trouble. 

But backing it up won't hurt either :)

---

### Post by westyonfire on 2007-11-11
bulldog,
I did the dpkg-reconfigure xserver-xorg command and answered all the questions best i could. i typed reboot when it was finished and booted back up with the normal first option; no change. still freezes on the orange screen. now trying with the rest of the stuff. brb

edit: oops i got that wrong. after the "dpkg-reconfigure xserver-xorg" command it freezes at the same place except the screen is black..the orange never loads up but the mouse cursor behaves the same.

---

### Post by P4man on 2007-11-11
Hmmm.. if you selected "vesa" when executing "dpkg-reconfigure xserver-xorg", my method will not yield much either, since its only intended to load the vesa driver, which would already be the case.

---

### Post by westyonfire on 2007-11-11
IT WORKED!!! i love you guys!
I dont get it, i put vesa in the 'dpkg-reconfigure xserver-xorg' thing and it didnt work. but this time it did??? and youre saying i just did the same thing...hmm
also does this mean ill have to go without 3d acceleration? If so will there be an update sometime in the future to fix this or will i be unable to unleash this compiz stuff until i get a new pc or graphics driver?

thanks so much for your help guys.

---

### Post by bulldog on 2007-11-11
Depends on your graphics.
If you have a supported graphics,you can install a driver and enable the candy.

---

### Post by westyonfire on 2007-11-11
so if i find a driver for my radeon m9200 it will change the driver back from vesa to an ati or radeon one...which will potentially give me the same problem?

---

### Post by P4man on 2007-11-11
Glad it worked. But you are not there yet :)  Go ahead and try to install ATI drivers. I am going by the assumption Ubuntu tried to load the opensource drivers, and these failed, so try the ones from ATI themselves:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

If I remember correctly, they have a nice graphical installer

---

### Post by westyonfire on 2007-11-11
I went to the link...and the oldest radeon mobility driver they support is the 9600...bummer. oh well, I'm just glad you guys helped me get ubuntu working. I can wait til i get a new pc for the extra trinkets...xmas is not far off ;)

thanks again

p.s. this was my first post using linux and ubuntu. i guess i should let my brother have his pc back now...

---

