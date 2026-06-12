---
title: "dual boot with OS X and no boot chance from ubuntu"
date: 2011-04-30
forum: Apple Hardware Users
---

### Post by teugon on 2011-04-30
I've got a macbook 5.2 so I used the guide to install ubuntu 10.10 provided by

[https://help.ubuntu.com/community/MacBook5-2/Maverick](https://help.ubuntu.com/community/MacBook5-2/Maverick) 

anyway I installed ubuntu 11.04 but this wasn't a problem, I could make all the steps to install (I also used refit).

After that I started to fix the bunch of thing like F2 keys, trackpad, audio etc etc following the guide, 
grub now is default using the maxcpus=1

After I restarted I my screen used a bit of fantasy to tell not to boot. I'll enumerate all of them:

-  instead of show me the icon with "ubuntu 11.04 which is loading etc  etc"  I see the black screen with some outputs on the first line there  is a fsck of my ext4 partition which gives no problem then another thing  and the third and last one is something about supporting something.  when also the third one is done it happens nothing I got the screen with  output and I know is I can push the shout down key and system starts to  halt.

-  another possibility is that I see the icon with "ubuntu-only written"  and it sounds strange to me since it always shows the version and the  points under it which are all colored like if it is going to show me the  login panel. The problem is that it keep that forever and don't output  anything else(I waited 3 mins) 

-  the last one show me also the version number but it behave like the previous one

Another strange thing I've noticed is also the red light coming from the  headset jack. it seems that it's common problem which can be solved  with a stick:
[http://forums.macrumors.com/archive/index.php/t-237405.html](http://forums.macrumors.com/archive/index.php/t-237405.html)

Anyway it never happened before but when I try to boot from ubuntu,  sometimes it does. and It does only after I tried to fix the glichy  things using the forums advices:
[https://help.ubuntu.com/community/MacBook5-2/Maverick](https://help.ubuntu.com/community/MacBook5-2/Maverick)

The only thing I've not done so exactly was on section TRACKPAD where it says: "Then, edit your  /etc/X11/xorg.conf : "

it says to put:
Section "InputDevice"     Identifier     "Mouse0"

but I left it be:
Section "Inputs"     Identifier     "defaults"

/---/                /---/

I've tried with both maxcpus=1 and/or acpi=off to boot.
   I don't really know what else to do to have ubuntu back


PS: 

I've launched utility disco from OS X partion and it says I cannot active linux-swap area neither the ubuntu one.
More funny is that it says my ubuntu partition is fat 32  -.- and if I try to verify it says:

Verifico volume &#8220;disk0s4&#8221;
** /dev/disk0s4
Invalid sector size: 0
Errore: this disk must be repaired. click on Repair Disk.

Dunno if this could be usefull btw I've got a feeling that if I "Repair the disk my ubuntu partition would rll become a mess for it says it's not ext4 but fat 32

---

