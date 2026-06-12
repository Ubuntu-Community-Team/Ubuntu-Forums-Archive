---
title: "novice virtualbox question"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by gcos7 on 2007-06-18
;)After running into problems with installing VMware server in 7.04 (which in turn messed up VMWare player I had installed), I took someone's advice and installed Virtualbox.  My laptop came with a restore CD, not an OS install CD, but it did take it in Virtualbox and load in Windows.  When Windows starts, it wants to run windows setup, but it blue screen's out sayng that a driver was unloaded before all operations were completed.   Can anyone give me ideas on how to get around this?

Thanks in advance!:)

---

### Post by ukripper on 2007-06-18
Run Virtualbox in Linux and install windows in that by cloning your current windows using Clonezilla and get rid of BSOD( it is most annoying thing in windows)

---

### Post by gcos7 on 2007-06-18
;)I am running Virtualbox in Linux, trying to run Windows in Virtualbox.  Since I seem to have some sort of problem when Windows is installed to the virtual drive, I'll try clonezilla and see if it helps me out.

Thank!;)

---

### Post by Seisen on 2007-06-18
Can you post what the error says, this would help out tremendously?

---

### Post by gcos7 on 2007-06-18
I really wish I could post the error message, or better yet a screen copy, but it goes to blue screen and then restarts so fast (we're talking maybe 2 seconds at most) I can't really read much.  I tried the screen capture from the "applications" menu, but even it doesn't get it.

After many times of this happening, the most I could see was a message about a driver being unloaded while it still had pending operations or some such thing.

I also looked at Clonezilla, and I may be dense here, but I don't see how to create a Virtualbox VDI file from an existing Windows partition using it.

If anyone is still following this thread, any help would be greatly appreciated!:)

---

### Post by ukripper on 2007-06-19
Windows Restore CD won't help in your case as it is restoring to Virtual drive whereas restore was created on physical drives. if the restore matches exactly the drives image it was taken from only then you can restore otherwise you would need a fresh Install CD to install Windows on virtual drive. Can you get hold of WINXP botable cd?

Clonezilla won't help here either as you need an exact match of your physical drive to put image on.

---

### Post by gcos7 on 2007-06-20
:KSOkey, I'll try this again.  I have a Gateway MX3215 laptop running dual boot Windows XP and Ubuntu 7.04.  I've tried VMplayer and Virtualbox, and finally went to VMserver as someone recommended I try it.  I tried creating virtual disk and installing Windows in to it from my restore CD (this is not an regular XP CD, but a CD provided by Gateway to run a system restore).  This restore process creates 2 partitions - 1 for system restore, 1 for "normal" Windows.  When I try to boot up the virtual machine in VMserver, Windows blue screens out when it starts up.  I suspect this has something to do with either there being a restore partition in the virtual disk, or that the hardware as mapped through VMware don't match those that it expects.

So, I went through creating another virtual machine, using the custom option and specifying my Windows partition as the physical disk to use.  Again, when I start VMware Server and start the virtual machine, Windows blue screens' out again when Windows is booting (I get the Windows XP screen temporarily).

Any help??  I'm at the end of my rope - I want to use Linux, but until a replacement for Family Tree Maker 10 is created in Linux, I need access to Windows.   I also need access to Windows for one other thing (yes, you can chuckle here!) - I need the shockwave player in order to be able to do the daily jigsaw.  I would prefer not to have to dual boot, running LInux as my OS and then just starting a VM when I need Windows.;)

Thanks in advance!

---

### Post by gcos7 on 2007-06-20
I just now noticed your reply, and I must say THANK YOU!!  I have not understood why this wasn't working until now - it makes perfect sense.  The virtual drive is obviously not the same size as the physical disk, and if the restore process expects such a disk, then it makes sense!  Now my only question is:  if I ever for some reason need to replace my hard disk, and I get one with different geometry, will my restore work then?? (I hope so, as I do plan on replacing my hard drive in the future with a larger and faster rpm drive.

Thanks again!;)

---

### Post by Bachstelze on 2007-06-20
The restore CDs were designed to be installed on your laptop's hardware, not on a virtual machine, so it's normal it doesn't work. And anyway, I'm not sure it would be legal to install Windows of it since you have only one license.

---

### Post by bodhi.zazen on 2007-06-20
Hmmm ...

Here is a guide for virtualBox : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

Networking is a mess (sorry), otherwise it is in good shape.

There is a section on converting your windows install :

[http://doc.gwos.org/index.php/VirtualBox#Convert_.28Migrate.29_your_Windows_Insallation](http://doc.gwos.org/index.php/VirtualBox#Convert_.28Migrate.29_your_Windows_Insallation)

---

### Post by bodhi.zazen on 2007-06-20
gcos7 : I posted in your other thread. I think they should be merged as it get confusing ...

HymnToLife : It depends, Microsoft changed the EULA since the last time I read it, or so I am told...

---

### Post by gcos7 on 2007-06-20
> **HymnToLife said:**
> The restore CDs were designed to be installed on your laptop's hardware, not on a virtual machine, so it's normal it doesn't work. And anyway, I'm not sure it would be legal to install Windows of it since you have only one license.

It would be on the same computer the license is for, so I see no problem.

---

### Post by bodhi.zazen on 2007-06-20
> **gcos7 said:**
> It would be on the same computer the license is for, so I see no problem.

You should read the EULA if you want to know what the terms of the agreement.

---

### Post by ukripper on 2007-06-20
In my opinion if you get different Hardisk and take backlkup of your current ubuntu filesystem and data or perhaps use clonezilla to create image and put the cloned image on new HDD and on previous HDD restore windows from your restore CD but then you have to make changes to grub and fstab to mount manually all partitions.

I would prefer this option :-

I would  buy a new HDD. restore winXp image on my original HDD and then install Ubuntu on my new HDD and restore from my previous ubuntu backup onto the new ubuntu installation as it will detect all fstab and grub entries automatically. 


If you want to minimise your cost third option is to get/buy windows XP cd.


Choice is yours!

---

### Post by gcos7 on 2007-06-22
I own Windows XP, it is already installed in another partition.  I am trying, via the VBoxManage commands, to use an already installed Windows installation in a virtual machine running in Linux.

---

### Post by ukripper on 2007-06-22
> **gcos7 said:**
> I own Windows XP, it is already installed in another partition.  I am trying, via the VBoxManage commands, to use an already installed Windows installation in a virtual machine running in Linux.

Never tried or heard that before to access XP partition through Virtualbox but do let me know if that works out for you I will add it to journal.

---

### Post by gcos7 on 2007-06-23
UKRipper -I did get this working, see this message thread:

[http://ubuntuforums.org/showthread.php?p=2878814#post2878814](http://ubuntuforums.org/showthread.php?p=2878814#post2878814)

---

### Post by ukripper on 2007-06-24
> **gcos7 said:**
> UKRipper -I did get this working, see this message thread:

[http://ubuntuforums.org/showthread.php?p=2878814#post2878814](http://ubuntuforums.org/showthread.php?p=2878814#post2878814)

Great job. If it is bit slow then perhaps add some more memory to your machine it will respond bit faster.

---

