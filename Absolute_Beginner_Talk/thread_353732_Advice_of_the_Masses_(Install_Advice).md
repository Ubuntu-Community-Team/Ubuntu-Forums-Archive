---
title: "Advice of the Masses (Install Advice)"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by mlissner on 2007-02-05
Hello, I'm looking into doing an installation for a friend, and he's a bit afraid that he will end up like me - working on his Linux computer all the time if I do so.

I want to install an OS for him that just works no matter what he wants to do. He doesn't do a whole lot of crazy stuff on his computer, but he does use Photoshop, Dreamweaver and Visual C++ Studio.

I've proposed the following four options (with pros and cons), which sounds most logical to you all:
1. Install dual boot with four partitions: Windows, Linux, /home and swap.
+  Windows works fine, Linux works fine; Fairly simple; Allows later choice of OS
-  Sharing docs is a bit more complicated; Each partition becomes limited in size; have to reboot to change from one to the other; have to install hardware in both Linux and Windows

2. Install Linux and run Windows virtually with all of it's programs running within that.
+  Linux dominates the system; Can remove Windows later
-  Windows runs slower, more complicated set up; more likelihood of crashes

3. Install only Linux and run Wine
+  Linux dominates the system; long-term simlicity
-  Windows programs are limited in functionality; steeper learning curve; more complicated to install programs

4. Install just Windows and forget it
+ Simple now
-  So much for Linux.

I'm pretty torn about it. I'd like to take the route of number one or two I think, but I don't know anything about either of them really. I've never installed a dual boot, or dealt with complicated partitioning, nor have I done squat with virtualizations.

The computer in question is a Dell laptop, with a pentium IV, 512MB of RAM, 60Gig HD.

Thoughts?

---

### Post by Hinko on 2007-02-05
Dual boot. It's easy, safe and it doesn't prohibit the use of other options. You can still run VMware or Wine. And if he doesn't like linux, for whatever reason, he can allways easily go back.

---

### Post by mr.v. on 2007-02-05
> pentium IV, 512MB of RAM
I wouldn't suggest virtualization on that hardware exclusively. It's probably already running windows XP somewhat slowly without adding the overhead of virtualization. Try it and see, but I wouldn't rely on that for a configuration...

---

### Post by Bagboy23 on 2007-02-05
I voted just install Windows and be done with it. The reason is simple. 

I see no advantage of adding a Linux OS if your friend is not going to use it. His applications are all Windows based so it will just be a waste of HDD space. Granted he may tinker with it here and there, but for practical reasons I would just drop it. Alternatively, you could install Linux on Windows via Vmware and let him tinker with it there. He could also delete the Vmware partitions as he pleases if he wants to.

Linux isn't the be all and end all of everything. It has its uses but so does Windows. Go with what you **need**.

---

### Post by purdy hate machine on 2007-02-05
> **Bagboy23 said:**
> I voted just install Windows and be done with it. The reason is simple. 

I see no advantage of adding a Linux OS if your friend is not going to use it. His applications are all Windows based so it will just be a waste of HDD space. Granted he may tinker with it here and there, but for practical reasons I would just drop it. Alternatively, you could install Linux on Windows via Vmware and let him tinker with it there. He could also delete the Vmware partitions as he pleases if he wants to.

Linux isn't the be all and end all of everything. It has its uses but so does Windows. Go with what you **need**.

Agreed, stick with Windows. If your friend is curious about Linux give him a live disk to play around with for a couple of weeks first, if he decides it’s not for him then its no loss.

---

### Post by darrenm on 2007-02-05
VM windows would run fine on that hardware. Unless you need 3d acceleration install WinXP on vmware then boot it up when needed.

---

### Post by Spr0k3t on 2007-02-05
I say go with a dual boot system.  All of the listed apps and languages translate easily into Linux.  I believe once he has a taste for the differences in Linux, the Windows side will hardly be used.  I completely ditched the windows side and only keep a 10GB partition to load games if needed.

---

### Post by jvc26 on 2007-02-05
Dual boot or just mess with the live cd would be my take. If you install linux unless he is particularly interested in trying it out he may never use it and it be a waste of space and time. If he tries the live cd and likes it, installs it and then tries using it it may be more successful. The live cd admittedly won't run as fast as the full install, but for use of photoshop, esp. if he's a major user he will probably want to keep windows as photoshop CS2 doesnt run amazingly if at all in wine (i think 7 works alright, but not sure)
Il

---

### Post by reacocard on 2007-02-05
Dual boot is the best way to go for now. If your friend wants to switch entirely to linux later, you can easily set up VMWare or Wine for him then, but it's not as easy to go the other way.

---

### Post by deadgobby on 2007-02-05
I would go with the dual boot. Some people use Ubie to surf and read email with out the big worry of spy ware, making the system a Zombie, and not worry about installing a virus. If you friend wants to learn a new O/S. Your friend can can explore at their own pace.
Gobby

---

### Post by xpod on 2007-02-05
Why dont you just give your pal a couple of live cds to play with & bookmark some relevant sites for him then worry more about getting your own pc into a state they envy as apose to a state they fear:) 

I too had this wonderful notion at the start to spread the word and have all my friends & family using ubuntu but it`s a crazy idea when your just learning yourself and the best thing you can do is worry about your own Ubuntu and make it into something they cant help but want.

EDIT: IT was a "crazy" idea for me that is:-)

---

### Post by mlissner on 2007-02-07
Hey, thanks for all the great replies. Very useful just to get opinions even if it seems like the forum has heard the same question before.

In the end I did the dual boot solution, and things are working fairly well. It's been complicated. I wanted to set up four partitions like so:
1 - Windows 20GB (NTFS)
2 - Ubuntu 15GB (EXT3)
3 - Swap 750MB (SWAP)
4 - /home 85.25GB (FAT32)

For some reason though, the Ubuntu installer wouldn't have anything to do with FAT32, so I installed the /home area as ext3, thinking that the Windows drivers would let me communicate with it. 

Well, after a few hours and several hackneyed tools, I decided that the shared partition /home had to be FAT32 so both could talk to it, and I put in my knoppix cd, and switched it over with gtparted, which of course ruined the Ubuntu installation I had.

After that, I reinstalled Ubuntu so that my final result is this:
1 - Windows XP 20GB (NTFS)
2 - Ubuntu 15GB (EXT3)
3 - Swap 750MB
4 - Storage space FAT32

Seems to work well. The storage space partition is seen in Windows and Ubuntu without any extra work, but I would have preferred if it could have been /home. I'm going to work on that tomorrow.

---

### Post by housam on 2007-02-07
I voted for the dual boot as it is the best for the newbies till they get used to ubuntu.

---

### Post by reacocard on 2007-02-07
> **mlissner said:**
> Hey, thanks for all the great replies. Very useful just to get opinions even if it seems like the forum has heard the same question before.

In the end I did the dual boot solution, and things are working fairly well. It's been complicated. I wanted to set up four partitions like so:
1 - Windows 20GB (NTFS)
2 - Ubuntu 15GB (EXT3)
3 - Swap 750MB (SWAP)
4 - /home 85.25GB (FAT32)

For some reason though, the Ubuntu installer wouldn't have anything to do with FAT32, so I installed the /home area as ext3, thinking that the Windows drivers would let me communicate with it. 

Well, after a few hours and several hackneyed tools, I decided that the shared partition /home had to be FAT32 so both could talk to it, and I put in my knoppix cd, and switched it over with gtparted, which of course ruined the Ubuntu installation I had.

After that, I reinstalled Ubuntu so that my final result is this:
1 - Windows XP 20GB (NTFS)
2 - Ubuntu 15GB (EXT3)
3 - Swap 750MB
4 - Storage space FAT32

Seems to work well. The storage space partition is seen in Windows and Ubuntu without any extra work, but I would have preferred if it could have been /home. I'm going to work on that tomorrow.

/home can never be fat32, that's just a limitation of linux. You can, however, get windows to read ext3. Just install ext2ifs: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by mlissner on 2007-10-18
That driver didn't work for me when I installed it...not sure why.

As an update, it looks like the dual-boot was the wrong way to go. By giving the user this choice, I pretty much convinced them to use Windows nearly all the time. It just took too much effort and consideration to boot/learn Ubuntu.

Oh well.

---

