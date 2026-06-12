---
title: "planning out partitions before i reformat"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by yellowband on 2007-04-08
Hi
I'm getting a new laptop with a large hard drive. i want to have win xp, vista and ubuntu on it. i also want a fourth partition that has my personal files which will be independant of all the OS's. 

I have the gparted partition live cd, and i want to set up the partitions before i install the os's.  Can somebody have a look at my scheme and point out any potential pitfalls?

hda0 = vista (30 GB)
hda1 = xp (20 GB)
hda2 = ubuntu (20 GB)
hda3 = my files (90 GB)
----------------------------------
total = 160 GB

Would this setup work?  I remember the last time i installed ubuntu i needed extra partitions for a swap space and stuff. Do i have to account for that here?  should the swap partition be hda3 and  my personal files be hda4?  Are there any other sneaky partitions that i'm missing?

Finally , if i install vista, then xp, then ubuntu, will GRUB find and display all 3? 

thanks for any help.

---

### Post by floke on 2007-04-08
hda3 would have to be an extended partition with 2 logical partitions inside it: hda4 and hda5 - one would be swap and one would be your home dir.

Not sure how easy it will be to install XP and Vista in their own limited partitions since they both like to stretch out, but I'm sure that it can be done. Whichever - I would install Ubuntu last since this should pick up the others.

Good luck

---

### Post by Happy_Man on 2007-04-08
Grub will find all of them, yes. Just remember to install Ubuntu last, otherwise Microsoft will overwrite GRUB and you'll be annoyed. This site is good for any partition questions you may have: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Hope this helps!

---

### Post by rsambuca on 2007-04-08
I would consider switching the order of XP and Vista to make things easier.  Also, like the last poster, you will be making hda3 into an extended partition, with 2 logical partitions for your swap and root '/' directory.

You'll want to install XP first, then Vista, then ubuntu last and you shouldn't have any problems.  I currently have XP, Vista, ubuntu 32-bit, ubuntu 64-bit, ubuntu 64-bit Feisty, and Sabayon.

---

### Post by yellowband on 2007-04-08
cool, thanks for the help, i think i understand.

The only thing i'm confused about is what you guys mean by my home diredctory.  I understand about how the last partition will be exteneded (because of the 4 partition limit), but does that count as a partition? in other words is it going to look like this?

hda1 (logical) = ntfs for xp
hda2 (logical) = ntfs for vista
hda2 (logical) = ext3 for ubuntu
hda3 (extended):
     hda4 (logical) = swap for ubuntu
     hda5 (logical) = ntfs for my personal files.


Also i'm confused about how you say to use hda5 for my home directory (which i assume you mean for ubuntu). I want a partition that will hold my files global to all OS's, and my /home/user dir specifically in ubuntu to be mounted in ubuntu.  Therefor do  i need to make a partition for my home directory, or will ubuntu take care of that automatically?  

In other words if i made hda5 my home directory in ubuntu, i wouldn't be able to access it from windows as windows does not support that type of filesystem.

---

### Post by Happy_Man on 2007-04-08
Ah, but fs-driver.org has ext3 drivers for Windows. Therein lies the usability of the concept, you see.

---

### Post by bulldog on 2007-04-08
Ok,it should look like this,you don't have to be worried about the number of the partitions,this comes automatically.

hda1 (primary) = ntfs for xp
hda2 (primary) = ntfs for vista
hda3 (primary) = ext3 for ubuntu (10GB)
hda4 (extended):
hda5 (logical) = swap for ubuntu (1GB)
hda6 (logical) = ntfs for my personal files

When we talk about /home it means a separate partition which holds all your personal files and program preferences you'll use in Ubuntu,this should be an ext3 file system not NTFS.
But if you don't make a separate /home,it will be created by ubuntu within the / root system.
You only have to make sure this / root partition isn't too small,I would suggest minimal 10GB.

You should know ubuntu isn't capable to write to a NTFS file system,but it can read it without a problem.
So if you want to make a separate partition which can be used by all your OS's,it should be a FAT32 partition instead of NTFS.

---

### Post by yellowband on 2007-04-08
hmmm i see.

so by doing this i could see my ubuntu home directory in windows and use that insted of "my documents, my music etc...) what a clever idea..
that would make my home directory / personal files easy to back up in case o f OS corruption.  thanks!

---

### Post by Patrick K on 2007-04-08
Maybe this is the setup you're looking for:

hda1 (primary) = ntfs for xp
hda2 (primary) = ntfs for vista
hda3 (primary) = ext3 for ubuntu (10GB) (this is for the OS and global files, the "/" root directory)
hda4 (extended):
hda5 (logical) = swap for ubuntu (1GB)
hda6 (logical) = ntfs for my **shared** files (You'll need to install extra software for Linux to write to ntfs. You could make it FAT32)
hda7 (logical) = ext3 for /home (this is for your personal settings and files in Linux)

Note that the order of the partition inside the extended partition are immaterial and they will likely be named something different when you finish.

---

### Post by yellowband on 2007-04-08
great!! thanks for the tips

one more thing, you suggested allocating 10 GB to the / directory for ubuntu OS.  I was having a lot of trouble deciding on how large to make each OS partition. Would 10 GB be large enough to hold a lot of programs? I use most of the basic desktop apps plus development tools (C++ compilers, HTML editors, maybe even GIMP etc).  HOw about windows? what is a good size for the OS?  again i need space for my adobe products and maybe even eclipse / ms visual studio. I always pick a bad size for my OS's, too much or too little. keep in mind i'll minimal personal files on these partitions, only space needed is for programs.

---

### Post by muzzz on 2007-04-09
If you're worried about the space to assign to partitions, keep some unallocated. When I first installed an ubuntu/winxp dual boot I used the following scheme:

hda1 - 10 GB NTFS (WinXP)
(4.6 GB unallocated)
hda4 - 10 GB FAT32 (OS independ files like music, movies, cd images, etc.)
(4.6 GB unallocated)
hda3 - 7 GB EXT3 (ubuntu)
hda2 - 1 GB Linux swap

This allows me to "grow" my 3 major partitions in pretty much any way I see fit. I'm not 100% sure how best to achieve it with the number of partitions you're looking at.

Hda1 is a fairly clean WinXP Pro installation. Mainly just some small utilities and a few old games. It only uses ~5.5 GB, of which ~2.5 GB is the windows directory. Hda3 is a mess. Since this is my first linux, I installed dozens of things just to try them out. Notable things include the full ubuntu, kubuntu and xubuntu desktop packages, JDK6, netbeans, azureus and kdevelop. It uses ~4.2 GB

I can't really give a good estimate as to what you'll need, especially since I haven't used Vista yet. If you feel comfortable resizing your paritions later on I'd say start with about 10-15 GB for XP and 7-10 GB for ubuntu. Add a little if you don't like to clean your drive regularly.

---

