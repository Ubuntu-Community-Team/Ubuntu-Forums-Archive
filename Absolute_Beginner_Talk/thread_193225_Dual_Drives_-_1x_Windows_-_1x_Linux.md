---
title: "Dual Drives - 1x Windows - 1x Linux"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by Megadeth on 2006-06-09
Hi guys,

So, I always used LiveCD's before but I decided to install it on my small hard drive. The problem is, I'm a noob and I have several questions that many people answered with totally different answers and now, I'm all confused. I don't want to mess up everything because I don't own a Windows CD.

So, coming to the idea of installing Linux on my other drive kills me a little. This drive actually is a big NTFS partition (the whole drive is 1 partition). As I know Linux's have difficulties to resize or delete and even detecting them. So I have a question about that. Should I use Partition Magic to delete that NTFS partition and create the Linux's partitions on it (or just delete the NTFS and leave it without partitions so the Linux installer could just add the Linux's partitions), or use the Linux installer anyway ??

Thank you guys for you help :)

---

### Post by u.b.u.n.t.u on 2006-06-09
ubuntu can easily wipe NTFS or any other file system during the install process. The default file system for ubuntu is ext3, which in my view is more advanced than NTFS. How so? Well you will not need to defrag an ext3 HDD. The same isn't true for NTFS.

ubuntu uses the gnome desktop environment. That uses gparted as the equivalent to Partition Magic. gparted is an excellent program. If you are working on a HDD that does not contain Windows and is empty then you are safe to experiment.

I use gparted to wipe NTFS HDDs and format with ext3.

If you have 2 HDDs, then keep your Windows setup as is, and just install ubuntu on the other with ext3. Just make sure you are up to speed on using the boot manager.

---

### Post by confused57 on 2006-06-09
[QUOTE=Megadeth]Hi guys,

So, I always used LiveCD's before but I decided to install it on my small hard drive. The problem is, I'm a noob and I have several questions that many people answered with totally different answers and now, I'm all confused. I don't want to mess up everything because I don't own a Windows CD.

So, coming to the idea of installing Linux on my other drive kills me a little. This drive actually is a big NTFS partition (the whole drive is 1 partition). As I know Linux's have difficulties to resize or delete and even detecting them. So I have a question about that. Should I use Partition Magic to delete that NTFS partition and create the Linux's partitions on it (or just delete the NTFS and leave it without partitions so the Linux installer could just add the Linux's partitions), or use the Linux installer anyway ??

Thank you guys for you help :)[/QUOTE]


Since you don't own a Windows CD, you can install Ubuntu on the 2nd HD without touching the Windows drive using this method:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot)

---

### Post by Megadeth on 2006-06-09
[QUOTE=confused57]Since you don't own a Windows CD, you can install Ubuntu on the 2nd HD without touching the Windows drive using this method:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot)[/QUOTE]

Quite difficult for a noob, don't you think ? lol :rolleyes:

Anyway, only my Windows drive has a jumper, my Linux doesn't have any, so the Linux is automatically set in slave.

But anyway, I was kinda going with the idea of setting my BIOS everytime I want to change since I'm not that lazy and that I won't change of OS 1000 times a day. :rolleyes: My question about that is, does GRUB installs itselfs automatically or I need to install it ? Maybe somebody could tell me what to do so that GRUB doesn't install itselfs.

---

### Post by confused57 on 2006-06-09
If you can get an alternate install cd, you can consider this method, installing Ubuntu on "hdb" & grub to floppy to boot Linux, the desktop(livecd) cd doesn't give you the option of where to install grub:

[http://www.ubuntuforums.org/showthread.php?t=188819](http://www.ubuntuforums.org/showthread.php?t=188819)

There are no guarantees this will work, maybe someone else has a better idea.

---

### Post by Megadeth on 2006-06-09
[QUOTE=confused57]If you can get an alternate install cd, you can consider this method, installing Ubuntu on "hdb" & grub to floppy to boot Linux, the desktop(livecd) cd doesn't give you the option of where to install grub:

[http://www.ubuntuforums.org/showthread.php?t=188819](http://www.ubuntuforums.org/showthread.php?t=188819)

There are no guarantees this will work, maybe someone else has a better idea.[/QUOTE]

But I don't want GRUB. Can I just not install it ?

---

### Post by confused57 on 2006-06-09
It's my understanding that you have to have some kind of boot manager to bootup any OS, Ubuntu happens to use Grub.   Windows boot manager is located in the boot.ini file...which you don't want to edit or your Windows may be rendered unbootable.

---

### Post by Megadeth on 2006-06-09
[QUOTE=confused57]It's my understanding that you have to have some kind of boot manager to bootup any OS, Ubuntu happens to use Grub.   Windows boot manager is located in the boot.ini file...which you don't want to edit or your Windows may be rendered unbootable.[/QUOTE]

lol :oops: 

What I meant is, can I just don't install GRUB in order to simply use my BIOS to set the drive (Windows or Linux) I want to run ???

---

### Post by confused57 on 2006-06-09
[QUOTE=Megadeth]lol :oops: 

What I meant is, can I just don't install GRUB in order to simply use my BIOS to set the drive (Windows or Linux) I want to run ???[/QUOTE]

I'm not sure, I don't think so...but I've been wrong before.  I know you're new at this and I don't know how comfortable you are about opening up your computer, but you could just disconnect the Windows drive(disconnect both the IDE connection and the power connection)...then install Ubuntu to your second drive, reconnect your Windows drive, then use bios to select which drive to boot to.  In case you're not sure, the master drive is the connection on the end of your IDE cable and the slave IDE connection is the one located between the MOBO and master IDE connectors...that's about the only options I have, you may want to wait to see if someone may have any better suggestions, I'm pretty new at this myself.  

If you do this, make sure you don't touch anything else inside your computer...by all means unplug and disconnect everything attached externally to your computer before opening it up...touch the power supply to dissipate any static electricity, then just disconnect the master drive.

---

### Post by Megadeth on 2006-06-09
[QUOTE=confused57]I'm not sure, I don't think so...but I've been wrong before.  I know you're new at this and I don't know how comfortable you are about opening up your computer, but you could just disconnect the Windows drive(disconnect both the IDE connection and the power connection)...then install Ubuntu to your second drive, reconnect your Windows drive, then use bios to select which drive to boot to.  In case you're not sure, the master drive is the connection on the end of your IDE cable and the slave IDE connection is the one located between the MOBO and master IDE connectors...that's about the only options I have, you may want to wait to see if someone may have any better suggestions, I'm pretty new at this myself.  

**If you do this, make sure you don't touch anything else inside your computer...by all means unplug and disconnect everything attached externally to your computer before opening it up...touch the power supply to dissipate any static electricity, then just disconnect the master drive.**[/QUOTE]

Don't worry, I know that ;)

But as the way of installation you're telling there, does it works with the Linux drive in slave ? Because I can't set it in master because there is no jumper on it.

---

### Post by confused57 on 2006-06-09
Sorry, I didn't know how much you knew about computers, but it's good that you're comfortable disconnecting drives.  If there is nothing you mind losing on the slave drive, you can try what I suggested about just disconnecting your Windows drive and installing Ubuntu with just the slave drive connected.  I don't know for sure if it will work, but you won't know until you try it...if that's what you want.

---

### Post by Megadeth on 2006-06-27
[QUOTE=confused57]Sorry, I didn't know how much you knew about computers, but it's good that you're comfortable disconnecting drives.  If there is nothing you mind losing on the slave drive, you can try what I suggested about just disconnecting your Windows drive and installing Ubuntu with just the slave drive connected.  I don't know for sure if it will work, but you won't know until you try it...if that's what you want.[/QUOTE]

Can somebody tell me if it works ?????


EDIT: From my point of view. I'm thinking about installing GRUB after all, but is it really safe ??? Is there any chance it could mess up my MBR ?? Because I don't have any Windows CD, it could kill me...

---

### Post by Drakkor on 2006-06-27
Even if you set the bios to boot one or the other OS, you're still going to have to have grub to boot Ubuntu. I have 2 Hdds, first,an 80Gb,with XP on it, second drive with Ubuntu,dual booting with grub on the mbr. Even in a case like this,to change it back to booting just windows you can  just put the windows xp disk in and boot from it,then select "R" for repair,and then type "fixmbr" and a new master boot record will be created to only load xp at startup. Can you "borrow" an Xp disk if you want to change back ?

---

### Post by Megadeth on 2006-06-27
[QUOTE=Drakkor]Even if you set the bios to boot one or the other OS, you're still going to have to have grub to boot Ubuntu. I have 2 Hdds, first,an 80Gb,with XP on it, second drive with Ubuntu,dual booting with grub on the mbr. Even in a case like this,to change it back to booting just windows you can  just put the windows xp disk in and boot from it,then select "R" for repair,and then type "fixmbr" and a new master boot record will be created to only load xp at startup. Can you "borrow" an Xp disk if you want to change back ?[/QUOTE]

Maybe... But does GRUB is **THAT** safe ?? If so, I'm just going to install it.

---

### Post by Drakkor on 2006-06-27
No problems here,had Ubuntu a little over a week now and still have the options at startup to either boot Ubuntu....default or other operating systems.....XP.

---

### Post by Megadeth on 2006-06-27
Other people's opinion would be quite welcome :)

---

### Post by nowadays who knows on 2006-06-27
No problems dual booting with grub . There are suprisingly a lot of people who dual boot. One reason for me is I paid for xp and Im still going to use it since I paid for it already. Another is my wife is used to it so it stays. I use two hard drives one for xp and one for ubuntu. I even dual boot at work with ubuntu and xp with grub as the boot loader. Of course out of necessity I have edited my grub to boot xp by default but added another 5 seconds to select using my arrow keys as to which os I want .

Here is a link to a web page telling exactly how to edit the grub and boot windows first. or change the wait time before booting (so you get to choose.).8)

---

