---
title: "FC6 dual boot"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by epiphiny on 2007-02-12
Hi there, sorry if this has already been answered, but I promise I've tried to find some definitive answers!

I'm currently running FC6 on an IBM X206 server, 3GHz Pentium 4HT and 512mb ram.  For various reasons, I'd quite like to replace my current windows partition with an ubuntu one, and use vmware for all my windows things (seems to work well apart from a lack of usb in fc)

Unfrotunately i've run into a few problems

Firstly, ubuntu doesn't seem to like my ati radeon 9200 pro.  The liveCD boots to either a blank screen with 'signal over range' from the monitor itself, or to a blank screen with nothing at all, where ctl+alt+F1 etc has no effect.  This seems to be overcomable by installing the system in text only from the alternative cd, then using break=bottom in the kernal parameters to get to the command line and change xorg.conf to use vesa, where i can then play around with getting fglrx working.

Does anybody know how if this will actually work?

Also, I've been reading some worrying things about ubuntu's installer not playing nice with Grub and finding other linux partitions.  I know that its possible to recover grub, but im not sure im that confident and tbh would probably end up reinstalling fedora from backups.  Obviously I'd rather stick a fork in my eye, so if anybody knows any cast-iron ways of stopping ubuntu obliterating my boot partition I'd love to hear it.

Thanks in advance (the ubuntu community is defiantely better at helping with this sort of thing than the fedora one)
James

---

### Post by crispy_420 on 2007-02-12
Try booting into safe mode. You'll want to see if you can get vesa drivers going, no 3d but it will get you a gui. Maybe try the alternate install CD to do that.

As far as grub, that you will be stuck reconfiguring. I've never done it myself but the file is in /boot/grub, it's called menu.lst. It looks pretty straight foward though. I'm sure there are many guides here.

---

