---
title: "After install and reboot, no boot menu?"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Rictus on 2005-12-22
Hi, all. I downloaded the DVD version for AMD64, installed in on a second drive I just bought. Install seems to go fine. It asks if I want to install Grub or whatever it is, and then says to take out the disk and it reboots saying futher installation will be done on reboot. But when my computer reboots it just goes to windows xp like normal. The Ubutu drive then does not show up in my computer but it does in the disk manager which seems right. I tried it when I had the drive partitoned in half, when that didnt work I tried to install on the entire drive but same thing happens either way.
Well thanks.
Rick

Here is a copy of my boot loader if it helps.

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

---

### Post by Thunk on 2005-12-22
Your boot loader has nothing to do with it. The boot loadrer is an internal XP thing. Did you say "yes" to install GRUB? This is your real boot manager so it's critical that it is installed.

Ubuntu can share a drive or be on a totally separate one. As long as you have GRUB installed properly it should work just fine.

---

### Post by fordfan753 on 2005-12-22
How about changing your boot order in BIOS so that it boots off the Ubuntu drive rather than the Windows drive as default? I think what it's doing is booting from master hard drive (with windows on) and is totally oblivious to anything on the second drive, ie GRUB.

---

### Post by Rictus on 2005-12-22
hehe :oops: I edited the loader in then realized that later.
OK going to try boot order in bios, that sounds reasonable.

Well, it worked...sort of. Now I'm off to fix errors lol.
GLcore error...No screens found?
Thanks.

Double edit: looks like it might be pci-e ati cards that are the prob from this thread.

[http://www.ubuntuforums.org/showthread.php?t=93760&highlight=ati+x800](http://www.ubuntuforums.org/showthread.php?t=93760&highlight=ati+x800)

---

### Post by fordfan753 on 2005-12-22
That wouldn't surprise me, ATI linux support is a little limited compared to nVidia.

---

### Post by Rictus on 2005-12-23
Ya, I also have an AMD64 which was causing conflicts with the video card I guess. I ended up just going with the standard install instead of the 64 bit.

---

