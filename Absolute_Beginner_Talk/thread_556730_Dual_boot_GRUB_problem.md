---
title: "Dual boot GRUB problem"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by VegasDave on 2007-09-21
I installed Ubuntu a while ago on my XP machine in a dual boot configuration.

All was peachy until today when I was in Ubuntu and allowed some updates. On my next reboot, XP was gone from the GRUB boot menu. I had to boot with a DOS CD and ran fdisk /mbr to get back into XP .

So I have 2 questions. How do I get GRUB back up and configured for the dual boot and how do I keep this from happening again on the next Ubuntu update?

---

### Post by kellemes on 2007-09-21
Burn [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and enjoy the magic fixing your problems.

---

### Post by Pumalite on 2007-09-21
Re-installing Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Once in Ubuntu, post:
sudo fdisk -lu
cat /boot/grub/menu.lst
blkid

---

### Post by Duck2006 on 2007-09-21
Edit your menu.lst file and at the bottom add the windoze entry

title windoze
root (hd0,0)
makeactive
chainloader +1

---

### Post by logos34 on 2007-09-21
Sounds like you had the XP entry in the wrong place, in which case all you needed to do was add it back to menu.lst after the update.

After you restore grub using the link Pumalite provided, put the windows entry back in menu.lst OUTSIDE the 'automagic' section.

[http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST](http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST)

> "...[P]ut operating system entries that are 'static' (in other words, ones that are not to be automagically updated), either above the start of the automagic kernels list or after it, but not in it.
You can paste your Windows entry here if you want Windows to be first in the list and boot by default.
Your Windows entry to be automagically deleted every time Ubuntu is updated with a new kernel if you paste it anywhere between the beginning and the end of the debian automagic kernels list. (Well, it shouldn't have been there in the first place). Many users don't understand that and blame GRUB or Ubuntu for their problems."

---

### Post by VegasDave on 2007-09-21
> Your Windows entry to be automagically deleted every time Ubuntu is updated with a new kernel if you paste it anywhere between the beginning and the end of the debian automagic kernels list. (Well, it shouldn't have been there in the first place). Many users don't understand that and blame GRUB or Ubuntu for their problems.

That's what I needed to know-

I got it figured out now, thanks all.

---

