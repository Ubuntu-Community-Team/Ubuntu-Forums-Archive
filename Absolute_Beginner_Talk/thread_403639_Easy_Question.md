---
title: "Easy Question"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by PowerPLay on 2007-04-07
OK,

I installed Ubuntu Feisty on my machine and quite liked it. So I'm in the middle of removing vista completely from my machine. I've already deleted the partition and half my Hard Drive is unallocated. Here's the easy part: I have a bookable Acronis Disk that I can Manage my disk with. What I want to do is resize my ext3 partition that Ubuntu is on, to take up the rest of the space on the hard drive. 

That's all fine and dandy except when I try it Acronis tells me that it will screw up the loader or something and I would have to reconfigure it in order to boot into my linux again after the resize. Well, this scared me cause I don't want to mess my install up. My question is: Is it true and if so what is it talking about and how do I go bout fixing it after I resize it. If there is an easier way of doing this that would be helpful too.

I've tried the Gparted Live CD, it boots to a black screen. I don't think that it has the capability to work with my graphics card. 

Thanks for any help.

-Cole :guitar:

---

### Post by msaied on 2007-04-07
what about Ubuntu live cd it contains Gnome partition editor
system->Gnome partition editor
unmount the drive then try to resize it .. be patient it takes some time

---

### Post by PowerPLay on 2007-04-07
I'll give that a show. Thanks.

-Cole

---

### Post by dwblas on 2007-04-07
I would think that you would delete the MSWindows partition first and then resize (although parted may do this for you), and this will "screw up the boot loader" because MSWindows won't be there, so you want to delete if from /boot/grub/menu.lst

---

