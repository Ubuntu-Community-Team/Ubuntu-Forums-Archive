---
title: "error 22?"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by minden on 2006-06-29
i _was_ dual booting xp and ubuntu.  i deleted my ubuntu partion because i was going to do other things with it.  now when trying to boot up i get an error 22.  i tried to use one of my live CD's to boot but it restarts the computer when "adding live cd user".  HELP!

---

### Post by catlett on 2006-06-29
You deleted grub when you deleted Ubuntu. Right now you do not have a boot loader to boot up XP. You can do 2 things. Reinstall Ubuntu or get a windows XP install disk. Boot to it. Select recovery mode by entering r at the first prompt.
It will take you through a quick dialogue eventually asking you which version of windows you want to use for the recovery. You only have 1 so enter 1 and it will give you a command line i.e. C:\
Enter this command there ```
fixmbr
``` This will rewrite the mbr with windows bootloader and you will be able to boot to XP like you did before ubuntu

---

### Post by coffeecat on 2006-06-29
I guess your error 22 is a Grub error. This from the Grub manual:

> 22 : No such partition

This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.Could you clarify what you are trying to do. You say you've deleted your Ubuntu partition, so is it Windows you are trying to boot into when you get this error? And I can't quite understand your last sentence.  Give us some more details about what is happening when you use a live CD.

---

### Post by minden on 2006-06-29
ok this is what i think will work, tell me if im incorrect.  

the dapper GUI install does not seem to be working so i am download a Hoary iso and i am going to try the text based install through that.

---

### Post by coffeecat on 2006-06-29
[quote=catlett]You deleted grub when you deleted Ubuntu.[/quote]

I don't think so. Error 22 really does sound like a Grub error. Perhaps minden could give more details. What happens? What do you see on screen?

---

### Post by minden on 2006-06-29
When just trying to boot i get this

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 22

and when i try a live cd it just crashes when load all the things that go by and say "ok"

---

### Post by minden on 2006-06-29
where is the grub boot loader located?

---

### Post by az on 2006-06-29
[QUOTE=minden]where is the grub boot loader located?[/QUOTE]
A small part of it is located on the mbr.  The rest is on a partition.  In your case, it is on the partition that you blew away.  That's what error 22 is!  (I can't find the rest of myself!)

You need to fix your mbr or install another OS that will detect other OSes on your box and add them to a bootloader, like ubuntu does.

---

### Post by minden on 2006-06-29
[QUOTE=azz]A small part of it is located on the mbr.  The rest is on a partition.  In your case, it is on the partition that you blew away.  That's what error 22 is!  (I can't find the rest of myself!)

You need to fix your mbr or install another OS that will detect other OSes on your box and add them to a bootloader, like ubuntu does.[/QUOTE]

ok
so installing hoary hedgehog will work?

what is mbr? <-- edit: occurred to me what it is after post

---

### Post by minden on 2006-06-29
since im not getting an answer on the hoary question...
i hope it works

---

### Post by catlett on 2006-06-29
Hoary will work. MBR is "Master Boot Record" it is exactly what it says, the place for the boot record.
Grub puts a small part on the mbr. It can only be a small part because the mbr is only 512bytes. The rest of grub goes into your boot partition or folder. You could make a boot partition and keep your boot folder,grub and kernels off your Ubuntu partition but if you followed a regular Ubuntu install all that stuff is on your boot folder on your ubuntu partition.
So to give you a rundown on error 22. Your system starts to boot. The bios starts your hard drive and acceses the mbr. grub stage 1 is on the mbr and is activated. Stage 1's job is just to connect to stage 1.5 where 1.5 takes over and activates the large section of grub.
When stage 1 couldn't find stage 1.5, because you deleted it with your ubuntu partition, it gave an error. Error 22 to be precise which means it can't locate stage 1.5.

So you need to reinstall an operating system that has dual boot capabilities (hoary will do) or you need to reinstall ntldr (windows bootloader) so you can boot XP. XP's command line isn't much to speak of but it has ubuntu with fixmbr. Ubuntu doesn't have such a command. fixmbr when entered from a command line in windows, rewrites the mbr with ntldr.

P.S. I don't post unless I know what I am talking about. If I don't know but am offering a hypothesis I will preface it with "I don't know but" or "this may work" or "I may be wrong" but if I give directions and commands it's because I know from experience or from documentation that it will work.

---

### Post by prophet11 on 2006-07-09
that fixmbr totally worked thanks..

i had the same problem i just took the partition off (stupid) if i want to take off ub from the other HD next time what should i do..

---

### Post by catlett on 2006-07-09
To avoid the loss of booting to windows when you erase ubuntu, you will need to install the recovery console to windows or boot to the recovery console and issue```
 fixmbr
``` It will probably be easier to install the recovery console to your system. That way it is an option when you start up. These are Microsoft's instructions.
> To install the Recovery Console as a startup option

1.
	

With Windows running, insert the Setup CD into your CD-ROM drive.

2.
	

CLick Start and select Run.

3.
	

Type the following where D: is the CD-ROM drive letter:

D:\i386\winnt32.exe /cmdcons

4.
	

Follow the instructions on the screen.

Note
•	

To run the Recovery Console, restart your computer and select the Recovery Console option from the list of available operating systems.
•	

You must be logged on as an administrator or a member of the Administrators group in order to complete this procedure. If your computer is connected to a network, network policy settings may also prevent you from completing this procedure.
•	

To see the commands available on the Recovery Console, type help at the at the console prompt.
•	

If your computer will not start, you can run the Recovery Console from the Setup CD. See Related Topics for information on running the Recovery Console when your computer will not start.  
Just for the sake of full disclosure, these are the instructions for starting the recovery console fron the cd 
> From the Setup CD-ROM 

1.
	

Insert the Setup compact disc (CD) and restart the computer. If prompted, select any options required to boot from the CD.

2.
	

When the text-based part of Setup begins, follow the prompts; choose the repair or recover option by pressing R.

3.
	

If you have a dual-boot or multiple-boot system, choose the installation that you need to access from the Recovery Console.

4.
	

When prompted, type the Administrator password.

5.
	

At the system prompt, type Recovery Console commands; type help for a list of commands, or help commandname for help on a specific command.

6.
	

To exit the Recovery Console and restart the computer, type exit.

If you have already installed the Recovery Console 

1.
	

During Startup, select Recovery Console from the startup options menu.

2.
	

If you have a dual-boot or multiple-boot system, choose the installation that you need to access from the Recovery Console.

3.
	

When prompted, type the Administrator password.

4.
	

At the system prompt, type Recovery Console commands; type help for a list of commands, or help commandname for help on a specific command.

5.
	

To exit the Recovery Console and restart the computer, type exit. 




Once you installed the recovery console or ran it from the cd and issued the fixmbr command, you will have ersed grub but you will have installed window's bootloader. You can now boot to windows as you did before you installed ubuntu.
The next step is to delete Ubuntu's partition. You can use window's disk management to delete and format the partition or you can use a 3rd party partitioner to delete, format and resize the ubuntu partition.
To get into Windows disk management go to Start<Control Panel<Performance and Maintenance<Administrative Tools<Computer Management<Storage<Disk Management. When you finally get there :D  your drive will look like a bar graph. Just right-click on Ubuntu's partition and select "delete". Then right-click again and select "format". The XP standard is NTFS.
You can also use 3rd party applications like Partition Magic (there is a fee) [http://www.symantecstore.com/dr/sat1/ec_MAIN.Entry17c?CID=219398&PN=5&SP=10007&SID=49997&PID=705807&API1=65&API2=GOOGLE&API3=partition_magic_exa&API4=Google&API5=www.google.com&CUR=840&DSP=&PGRP=0&ABCODE=&CACHE_ID=219398](http://www.symantecstore.com/dr/sat1/ec_MAIN.Entry17c?CID=219398&PN=5&SP=10007&SID=49997&PID=705807&API1=65&API2=GOOGLE&API3=partition_magic_exa&API4=Google&API5=www.google.com&CUR=840&DSP=&PGRP=0&ABCODE=&CACHE_ID=219398)
Or you can use the open source Live Cd Gparted Live (This is free but you have to download and burn the iso into a bootable cd rom) [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

In Conclusion, you do not have to be left with an un-bootable system when you remove Ubuntu. You have to do a little work though. You need to access windows recovery console by either booting to the install cd or installing it to your system from the install cd. Once in the recovery console issue the command fixmbr. Now you will be able to boot to windows but not to ubuntu any more.Once in windows use their disk management tools or a 3rd party application to delete and repartition the space ubuntu was on.

---

### Post by prophet11 on 2006-07-09
heh

[http://www.computerhope.com/fixmbr.htm](http://www.computerhope.com/fixmbr.htm)

"Repairs the master boot record of the boot disk. The fixmbr command is [SIZE="5"]only available[/SIZE] when you are using the Recovery Console"

youre probably right

---

### Post by Frank Golden on 2006-07-09
> **catlett said:**
> P.S. I don't post unless I know what I am talking about. If I don't know but am offering a hypothesis I will preface it with "I don't know but" or "this may work" or "I may be wrong" but if I give directions and commands it's because I know from experience or from documentation that it will work. Right on Catlett, I know this has been posted before but
anyone wanting to dual Ubuntu should read this.

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

Especially, I say again especially the section about removing
Ubuntu at the beginning.
This is an excelent source of info on dual booting Ubuntu
and contains a lot more general Linux info also.

We need to get bigpond's permission to post his tutorial "sticky".
Or something like that.

---

### Post by confused57 on 2006-07-09
catlett,
   Nice instructions

---

### Post by tigerfire on 2007-07-22
Yes, I've encountered this problem too.  My computer came with a sata drive which ubuntu 6.06 and 7.04 both identified correctly and installed as a scsi device.  Worked fine.  I then installed an 80 GB pata drive as a backup drive.  

When I went to reinstall Ubuntu (I wanted to try the 64bit version).  I kept getting the error 22: from GRUB.

I attempted the reinstall multiple time with various partitioning options.  All of my installs were attempted to the 250GB sata drive.  None of them worked.

I turned off the 80GB pata drive in the BIOS.  Gparted still detected the 80GB disk even though it couldn't access it for read/write/partitioning options.  An install with the 80GB pata disabled in BIOS still brought up GRUB error 22.

I unplugged power to the 80GB pata drive and the install worked fine the first time.

I suspect this has to do with how the Linux kernel handles hard disks?  The 80GB pata drive is always detected as the first drive in the system so if you install to a secondary drive such as a sata it still tries to load the kernel off the first detected hard drive in the system in this case the 80GB pata?  If you remove the disk, load the kernel so it only points to the only existing drive and then add the 80GB, it can be mounted successfully as a secondary drive?

I don't know enough about this process to be sure.  Anyone know more?

---

### Post by tigerfire on 2007-07-22
By the way.  I'm not running windows at all on this system (AMDx2 3600+ dual core).  I'm not interested on running windows on this system.  These have been installs with Ubuntu only.  The live CD cannot install/reinstall Ubuntu correctly to a system with both a sata and pata drive in the system where the install is attempting to be made to the sata device.  Don't know why.

---

