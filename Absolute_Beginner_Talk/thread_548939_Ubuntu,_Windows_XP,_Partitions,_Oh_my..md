---
title: "Ubuntu, Windows XP, Partitions, Oh my."
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by rjulian57 on 2007-09-11
From the tutorials online, Ive seen that Ubuntu automatically will partition your hard drive and dual booting is a cinch with XP. So, I decided to give it a go. I get to the install and the prompt doesn't look much like what the tutorial had (I think they were using the previous Ubuntu edition). Basically, I'm given the options of "Guided- Use entire disk", "Guided - use the largest continuous free space" (which does not work) , and "Manual".

If you're suggesting Manual, I have another problem, under the "free space" partition, there is only 8 MB, which is nowhere near enough that I need for Ubuntu. I'm hoping that I don't have to go the way of doing it manually, but it seems like that's all I have.

I'm running a Dell Inspiron 1501 with a 60 GB harddrive. It should be plenty to run Ubuntu. 

Thanks in advanced.

---

### Post by Maestro23 on 2007-09-11
Take a look at this for setting up a dual-boot system: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by rjulian57 on 2007-09-12
Thanks, but I'm not given the first option (the one suited for people who want to dual boot) and the third (manual) option is a little confusing to me. I'm wondering if I just decrease the size of one partition, if it will increase the amount of free space. Also, I wonder if there's anything I can do from windows to make the partitioning easier.

---

### Post by BrendanM on 2007-09-12
Your best bet it to boot to the Ubuntu Live CD, and then use GParted to resize the windows partition to create more free space.

You could also use partition magic or some other windows-based partitioning tool, but those usually cost money.

---

### Post by Shazaam on 2007-09-12
Defragment Windows before you resize it!

---

### Post by splintercellguy on 2007-09-12
> **Shazaam said:**
> Defragment Windows before you resize it!

I'm not sure that's required with the ntfsresize on the Ubuntu LiveCD, but it doesn't hurt.

---

### Post by lisati on 2007-09-12
> **Shazaam said:**
> Defragment Windows before you resize it!

And don't forget to make a backup of important data as well.

---

### Post by eentonig on 2007-09-12
If you wan to partition from within windows. You can always use PartitionMagic. But GParted does the same and faster.

As said before:
- Defragment your drive.
- Make a backup.

---

### Post by Overbyte on 2007-09-12
> **rjulian57 said:**
> If you're suggesting Manual, I have another problem, under the "free space" partition, there is only 8 MB, which is nowhere near enough that I need for Ubuntu. I'm hoping that I don't have to go the way of doing it manually, but it seems like that's all I have.

The 8mb free space is reserved by Windows for its er...partitioning needs.

You can:
A - resize the partitions to make room for one (easier)
B - wipe all partitions, set a strategy, and use the LiveCD to create the hard disk layout

Here's a site detailing strategies for partitioning:

[http://partition.radified.com/](http://partition.radified.com/)

In either way, yeah, backup the data first! ;)

---

### Post by rjulian57 on 2007-09-12
Thank you all so much for the responses. I've already defragmented, but will probably defragment again just to be sure. I have everything backed up, so no problem there either. I'll probably just go with your option A, Overbyte. I'm glad I have a livecd and am able to do this.

---

### Post by slira on 2007-09-12
Hi there
in my first attempt to install ubuntu (dapper drake) in my pc i faced the same problems you have.
the question is that windows xp always comes in one single partition... worst, the boot is normally placed in the middle of the disk..... no comments!

ways to deal with that: defragment (several times if needed); the green will show you where you must stop your resizing of the first partition; once I did it wrong and erased the windows (not a big lost, but annoying anyway :)

after you have your disk defragmented you can make another partition, or create free-space (non-allocated)  using a partition manager from inside windows... but this is not 100% safe... you risk loosing your windows.

Well,if you managed to create free space you can use the option "use the largest continuous free space", or you can do it manually; it's easy: 1 partition for root (at least 5 Gb); 1 partition for swap (1,5 x your RAM), 1 partition for home (the size you want for documents etc). 

EDIT: If you don't have enough space, you can make just a root and a swap partition and forget about the home one, home will automatically be placed in the root partition. Be aware that this will severely limit your space for documents and if you ever destroy the ubuntu partition you'll loose all the stuff you had saved.

Both ways work fine, BUT be careful doing it manually when asked about mounting points - do NOT chose the windows partition or you will destroy windows...

after install, reboot; hopefully you will see a boot screen (grub or other) asking what do you want to boot. Choosing linux you can edit the file menu.lst to customize that boot menu.

Other option (safer!); install Ububtu in an external usb HDD; it works fine! and you do not mess with your internal windows disk. (I have ubuntu in my machines in both ways)

enjoy Ubuntu :):):)

slira

---

