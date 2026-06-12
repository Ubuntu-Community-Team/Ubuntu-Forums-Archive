---
title: "P4m800 help"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by ebeard on 2007-11-19
I can't get openchrome to set up my VIA graphics again. I had it working once before in Edgy. Decided to try Gutsy ( big mistake, no start and kernal panics), Feisty doesn't work either, why couldn't I just leave it alone? Trying to now rebuild an edgy machine that worked as before (had to wipe partition and start over).

Anyway. I went through the install steps here [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome), manual install. It couldn't find the auto install thing. 

No blatant errors in terminal, but some may have scrolled by. When I changed the line in xorg.conf from vesa to via and restarted, no go. Had to edit back to vesa in nano. It acts like it can't find drivers. 

Here's the config lines

Section "Device"
Identifier  "Generic Video Card"
Driver      "vesa"
BusID     "PCI:1:0:0"
EndSection

Shouldn't there be a device "via" somewhere. I can't find it. Lspci shows unichrome IGP pro.

This worked before the upgrade , but now it doesn't. Any ideas?

---

### Post by deadgobby on 2007-11-19
If you have the Kernel Panic. That is not good... Not good at all!  I put at fault that I had  DA moment and did not disable the 3 party resources and second I I had to start from fresh. At least I had a slave drive with all my saved data. At least when I did a fresh install of 7.10, it pick up my slave drive and it  took all my Mozilla book marks. Sorry to give you bad bad news.
Gobby

---

