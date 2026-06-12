---
title: "some quick (I hope) noob questions related to GRUB"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by rache1111 on 2008-01-22
Hi,

I have some quick questions about ubuntu and I would really appreciate it if someone could answer them.

I currently have a dual boot setup with windows vista as the first partition (active) and ubuntu as the second partition(primary) using Grub. The grub settings is stored in /boot/grub/menu.lst. 

1. Would deleting my linux partition make my system unbootable? Because grub program actually reside in the ubuntu partition instead of MBR? Sorry if I am not making any sense, I still don't fully understand how MBR and the boot program GRUB really works.

The reason I am asking this question is because I am thinking about doing a fresh install of 7.1 instead of upgrading. I figured that installing over the top of the existing ubuntu would remove the settings I have set in menu.lst for grub.

2. Is there a way to make a "Live Grub CD" just so that I could boot into windows even if my linux installtion screws up?

3. How important is having a swap parition in Ubuntu now adays when most new computers comes with 2-3GB of ram? I have 2GB of ram, should I still bother to create a swap partition? I mean I don't create a swap partition for windows vista and it works fine, certainly the vista uses more memory than ubuntu right?


Thank you very much,

---

### Post by JoshuaRL on 2008-01-22
1.  Yes it might.  You would probably want to go ahead and to it, and come back here if you have any problems.  You can always edit Grub or use "fixmbr" in windows if it gets messed a little.

2.  Super Grub.  It helps with anything Grub related.  Even some of the mods here rave about it.  Not really a Live CD as I understand it, but should fix anything that goes wrong.

3.  Still pretty important.  From what I understand the system starts having instabilities if you don't have a swap partition.  I would seriously suggest against not running a swap partition.

---

### Post by tojge on 2008-01-22
Doing a clean install of a new version of (K)Ubuntu should not mess anything up. Sure, it will overwrite your previous settings, but it will configure itself correctly, just like it did the first time, so you should be able to boot into any OS you have installed without a problem.

Problem arises when you make a fresh install of Win on the computer that also has Linux installed, 'cos it overwrites the MBR with Win bootloader, which can only load Win (go figure), but it can be solved easily (in a manner of speaking) using a Live CD.

Swap partition IS very important, and by all means DO CREATE it!

PS The fact that you do not manually create swap partition for your Win installations does not mean they themselves do not create a so-called "page file", which is pretty much the same thing (well, at least it serves a similar purpose)

---

### Post by emarkd on 2008-01-22
An elaboration on 3:  Even though Windows doesn't use a swap partition, it still swaps data from RAM to disk using a swap file.  The linux way is much better because that huge swap file that Windows creates causes the disk to become fragmented more quickly because it has to write around that constantly changing file.  Linux moves the swap file into it's own partition and solves that problem quite nicely.

---

### Post by LaRoza on 2008-01-22
> **rache1111 said:**
> 
2. Is there a way to make a "Live Grub CD" just so that I could boot into windows even if my linux installtion screws up?

3. How important is having a swap parition in Ubuntu now adays when most new computers comes with 2-3GB of ram? I have 2GB of ram, should I still bother to create a swap partition? I mean I don't create a swap partition for windows vista and it works fine, certainly the vista uses more memory than ubuntu right?


Thank you very much,

2. See the link in my sig. The Super Grub Disk is a live disk which can do many things. It can restore the Windows bootloader for you. (In Advanced->Windows (Advanced))

3. Windows uses a page file, and it is sometimes quite large. It isn't on another partition, which is less stable. A small 512 MB swap would be good to have.

For Windows, one could move the swap file (or not use it) to another disk, which is a better arrangement really.

---

### Post by rache1111 on 2008-01-22
Thanks so much for the help you guys.

I have download super grub and it works great! 

I have some more questions related to linux swap.
How big should my linux swap be if my current system memory is 2GB? Do I have to do this before I do a fresh install or does the installer let me specify this optoin?

Thanks again,

---

### Post by sandysandy on 2008-01-22
> **rache1111 said:**
> Thanks so much for the help you guys.

I have download super grub and it works great! 

I have some more questions related to linux swap.
How big should my linux swap be if my current system memory is 2GB? Do I have to do this before I do a fresh install or does the installer let me specify this optoin?

Thanks again,

Generally SWAP files are twice ur RAM size. But since ur memory is 2 GB, lesser size should also be ok. The installer will let u specify the swap.

regards

---

