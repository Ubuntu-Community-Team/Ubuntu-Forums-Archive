---
title: "XP and Ubuntu"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Ultimate-one on 2006-09-14
i have to hard drives one is running windowsXP and the other is running Ubuntu.. i was told that the ONLY way to switch between the 2 is to reboot.....
is there another way to switch between the 2 without rebooting all the time??

---

### Post by JanLimpens on 2006-09-14
I am afraid not.

---

### Post by Spankmaster79 on 2006-09-14
> **Ultimate-one said:**
> 
is there another way to switch between the 2 without rebooting all the time??
Yes, choose the system you like most and then run the other one in vmware!!!:p 

No, seriously there is no way. Because this would mean both systems need to be up and running. As far as I know no way.

But correct me if I'm wrong.

---

### Post by xpod on 2006-09-14
You can have access to your windows partition and theres plenty apps that allow you to use your windows programs but i still think you have to reboot to actually get into windows.....i could be wrong

---

### Post by Leeghoofd on 2006-09-14
If you want to use the same DATA on Ubuntu as on XP, use part of your harddrive as "fat32" instead of the default "NTFS" of XP.
Instructions on how to do this can be found on this forum.

You cannot switch between operating systems without rebooting. ( unless you want to make use of Virtualisation software.

---

### Post by 23meg on 2006-09-14
Your options:

- Rebooting
- Virtualization (Xen, VMWare, QEMU, etc.)
- Two computers

---

### Post by whizbaby on 2006-09-14
Linux and XPensive running in parallel? Hell, no! Unless you write an OS especially for that purpose (but who wants to do that?). You can try to run essential(?) dozer programs in an emulator (wine) but that's it. Think about how essential your LoseDoze progs really are and if you can't replace their functionality in ubuntu so you won't have to switch. (BTW in virtualisation you won't have either of the OS run in a normal way (e.g. installing Applications gets different a lot). Looking at VMware you see that only the player is free.)

---

### Post by Ultimate-one on 2006-09-14
thanks for all the replys :)
very helpful site and people...thanks  :)

---

### Post by marklid on 2006-09-14
Get hold of VMWare Server (which is free) and you can create XP running within Ubuntu in a VMWare session.

Unlike VMWare Player, you can create new machines, change settings/confgurations etc.

I got sick of dual booting so went the whole hog with Ubuntu and use XP within VMWare for the Window$ apps I still need.

There's a lot of info around the foums for this - have a look around.

---

### Post by rcatman on 2006-09-14
If youre interested in using vmware go here:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

it's a very easy tutorial. I had vmware up and running in no time.

---

### Post by David Corrales on 2006-09-14
> **whizbaby said:**
> Linux and XPensive running in parallel? Hell, no! Unless you write an OS especially for that purpose (but who wants to do that?). You can try to run essential(?) dozer programs in an emulator (wine) but that's it. Think about how essential your LoseDoze progs really are and if you can't replace their functionality in ubuntu so you won't have to switch. (BTW in virtualisation you won't have either of the OS run in a normal way (e.g. installing Applications gets different a lot). Looking at VMware you see that only the player is free.)

Just as an interesting note, the VMWare people have the GSX server which runs on top of hardware and every other OS runs in a virtual environment. It has lots of uses for server consolidation, application testing, etc...

---

