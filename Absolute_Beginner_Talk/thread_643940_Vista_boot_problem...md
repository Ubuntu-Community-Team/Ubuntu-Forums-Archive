---
title: "Vista boot problem.."
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Crazymo on 2007-12-18
Hello...

I wanted to install ubuntu so i burned it on a disc. But after all i couldnt complete intallation cause it was stuck at 15% of the procedure. Now I dont want ubuntu anymore but want my old windows vista back, but it wont work anymore. It doesnt recognize vista at computer startup and i can only run Ubuntu from the live cd. btw, i had dual boot from win xp and vista before
My partition are like this atm:
unallocated      unallocated                                4.31 GB
/dev/sda2        extended                                123.68 GB                       lba
    /dev/sda5    ntfs               Windows XP          87.89 GB
    /dev/sda6    ntfs               Windows Vista      35.79 GB
unallocated      unallocated                               21.06 GB

Thanking you in advance

---

### Post by Severun on 2007-12-18
Did you try to completely power off your machine then count to 5 before installing Vista.  Sometimes the operating systems will leave your hardware in a state the other doesn't like.

Also you might want to try noapci as a boot option to get it past 15% on the Ubuntu install, that one has cause me problems more than once.

As to not wanting to use Ubuntu and go Back to Vista, I'm very sorry to hear that.  I went not just because it stays crunchy in milk, but on the 5 machines I have put it on so far, aside from the noapci issue,Ubutnu  was an easier install than Windoze XP.  I've heard tell that Vista aint all that and everyone I've talked to had to go through way more backbending to get it right.  It runs slower and is more bloated than anything before it,  if your still game..  Good luck with all of that...

---

### Post by Tristam Green on 2007-12-18
GRUB might be stuck.  Did you use the Bootmenu from XP or from Vista?  I don't know if they're the same or not, but if you can boot using a WinXP or other bootdisk you may be able to get to a command line and ```
fdisk /fixmbr
```

hope this helps:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)

---

### Post by Thelasko on 2007-12-18
Unfortunately you are asking a bunch of Linux experts how to boot Windows.
Pop in your Windows Vista install disk and select the "startup repair tool" option.  It should walk you through from there.  Then you can use Vista to repartition your hard drive the way you want it.

---

### Post by Niniel on 2007-12-18
Hello,

your installation problem may be caused by a faulty CD. Check your live CD for errors next time you pop it in (it's on the boot menu) and see if it finds any. You may just need to burn a new CD in order to be able to install Ubuntu.

---

### Post by Crazymo2 on 2007-12-18
Hello,

First of all, sorry for my late response but i had some problems with my password and i have created a new account atm and also many thanks to Severun, Tristam Green and Thelasko.

@Severun 
Do you mean noapci or noapic? I tried them both but it doesnt work :S

@Tristam Green
I cannot enter any windows

@Thelasko
I dont got vista cd.

The problem I got atm is that ubuntu is not installed on my pc.
I got "C:/" for windows xp en "D:/" for windows vista, but still i cant boot any of them and an only boot ubuntu from the live cd 7.10. I got a cd from win xp install and I tried it but there are missing files so that doesnt work neither. And I dont got a vista cd cause I have installed vista on D:/ while the setup was on C:/. 

PS: soz for my bad english 

Much thx

---

### Post by Crazymo2 on 2007-12-18
@Niniel

oooo.. I think youre right about the fault in the CD. I forgot it but there came an error, the error came when it was at 100% tho.. but that could be the problem.
btw, i cant burn anything, it cant even read a cd that i put in my drive.. it says unmountable drive.

I have also read some bootmenu at the startup of the pc when you install Ubuntu.. cant I get that without installing ubuntu...

I would like to have ubuntu, but i have to say that i dont wanna lose my windows vista for ubuntu.

---

### Post by rickycodie on 2007-12-18
@Thelasko
I dont got vista cd.


sorry there seems to be no helping unless you go back to ubuntu.

---

### Post by Crazymo2 on 2007-12-18
Back to ubuntu? I never had it and i want it. But at the moment i can't install it, I think cause the CD I have is not working properly and I can't burn a new cd cause I can only run from Live session user.

---

### Post by dstew on 2007-12-18
You can run a LiveCD Ubuntu session, right? If so, open a terminal and enter the command```
sudo fdisk -l
```and post the result. This will show the current state of your disk partitions. Maybe we can resurrect your Windows system.

I think your problem may be from your partitioning. If you never got past 15% of your installation, then the grub boot loader could not be the problem.

---

### Post by Thelasko on 2007-12-18
[http://www.bootdisk.com/]("http://www.bootdisk.com/") has some boot disks that might get you into windows again.

---

### Post by Crazymo2 on 2007-12-19
This is my sudo fdisk -l    :

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x64213596

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2             599       17752   129684240    f  W95 Ext'd (LBA)
/dev/sda5             599       12788    92156368+   7  HPFS/NTFS
/dev/sda6           12789       17752    37527808+   7  HPFS/NTFS

and i dont know if its a fault of the partitioning but i did.. automatic partitioning at the free space when installing and just like i said: when burning the CD he gave and error at 100% so maybe thats it.. ty for helping me

btw, Thelasko thank you for the site, ill try it when i can acces my brothers pc to set it on a disk.

---

### Post by dstew on 2007-12-19
From your fdisk table, it looks like you might have deleted a small partition at the front of your drive that booted Windows. It might still be possible to boot the second partition. However, it does not have a boot flag. That might be OK.

To try to boot the Windows partition, put the LiveCD and boot it. Open a terminal and enter these command:```
grub
```This should get you a grub command line, that looks like this:```
grub> 
```You can enter a series of commands here to try to boot your Windows system. The series of commands to try first are these:```
grub> root(hd0,1)
grub> makeactive
grub> chainload +1
grub> boot
```Let me know what happens.

---

