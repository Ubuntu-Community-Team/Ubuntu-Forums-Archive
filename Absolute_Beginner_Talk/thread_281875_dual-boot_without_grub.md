---
title: "dual-boot without grub"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by el_colombiano on 2006-10-21
I got some questions. First is when i start (only have win media center installed) I get ask if i want to boot windows media center or windows recovery will that have any affect when installing ubuntu?(just to let u know windows recovery is installed in a seperate partition and it cant be moved be partition magic i tried it and it is locked by hp and cant mess with it from windows)
 also i dont want to use grub to dual-boot could i not just add ubuntu to the list i get now(windows media center and windows recovery) if so how?](*,) 

ohh one last thing had 2 partitons a HP_PAVILION(C: ) and HP_RECOVERY(D: ) now i have those two as well as a linux ext3 (14 gigs)and linux swap(2gigs). I can see them all in partition magic but only C: and D: show when I open up my computer in windows should i be able to see the other two or no? ](*,) 

thanks

---

### Post by Sef on 2006-10-21
> I got some questions. First is when i start (only have win media center installed) I get ask if i want to boot windows media center or windows recovery will that have any affect when installing ubuntu?

GRUB should allow the choice of booting into Ubuntu or Windows.  Not sure if recovery will be seen, but it could be added.

> and it cant be moved be partition magic

PM and Linux don't get along to well.  When making a partition for Linux, use the one on the install disk or [GParted]("http://gparted.sourceforge.net/").

Note: GParted use a graphical interface like Partition Magic.

> also i dont want to use grub to dual-boot could i not just add ubuntu to the list i get now(windows media center and windows recovery) if so how?

Windows only boot to itself.  GRUB can boot into Linux or Windows.

> I can see them all in partition magic but only C: and D: show when I open up my computer in windows should i be able to see the other two or no?  

Delete the Linux Partitions that you made with PM.  Reinstall them with either the install cd partitioner or [GParted]("http://gparted.sourceforge.net/").

Note: GParted use a graphical interface like Partition Magic.

> linux swap(2gigs)

Swap should be twice your ram.  Over 1 gigabyte ram, you really don't need swap unless you are into gaming, video editing, or something else that is memory intensive.

---

### Post by gn2 on 2006-10-21
> **el_colombiano said:**
> I got some questions. First is when i start (only have win media center installed) I get ask if i want to boot windows media center or windows recovery will that have any affect when installing ubuntu?(just to let u know windows recovery is installed in a seperate partition and it cant be moved be partition magic i tried it and it is locked by hp and cant mess with it from windows)
 also i dont want to use grub to dual-boot could i not just add ubuntu to the list i get now(windows media center and windows recovery) if so how?](*,) 

ohh one last thing had 2 partitons a HP_PAVILION(C: ) and HP_RECOVERY(D: ) now i have those two as well as a linux ext3 (14 gigs)and linux swap(2gigs). I can see them all in partition magic but only C: and D: show when I open up my computer in windows should i be able to see the other two or no? ](*,) 

thanks

Do you have a Windows CD to re-install if things go wrong?

If all you have is recovery software on a partition, I would urge extreme caution before attempting a dual-boot on one hard drive.

If it is at all possible to add an additional internal drive I would suggest this method: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

If that is not possible I would advise using a USB drive and PCLinuxOS. Disconnect the Windows drive during install.

Then put the USB drive before the internal drive in the boot order, so that when you don't want to boot Linux, just disconnect the drive before booting.
(PCLinuxOS has an installer which will install to USB, and a GUI configuration tool for mounting Windows drives. Ubuntu does not.)

---

### Post by Sef on 2006-10-21
Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") to have a system with both Windows and Ubuntu on it.

---

### Post by gn2 on 2006-10-21
If you do not have removable restore media for Windows, be advised that what Sef is suggesting could leave you with a bill for a Windows CD.

Make absolutely certain ALL files and data you want to keep are backed up to removable media before you start.

Partition Magic is also a superior partitioning tool to gparted.

---

### Post by el_colombiano on 2006-10-21
thanks for the advice. I have read several tutorials on how to install. but i dont have a windows cd and have had some bad experiances with recovery cds. and the recovery partiton i cant do any thing to it from regular windows. its lock by hp. Hp does give me software to make system recovery disk but its only one set and i dont trust it. but i might have to do that.

I just had an idea could i make a partion for linux programs and just run a live cd(i have 2gigs of ram so it runs fast)?

---

### Post by Sef on 2006-10-21
> I just had an idea could i make a partion for linux programs and just run a live cd(i have 2gigs of ram so it runs fast)?

Yes, use [GParted]("http://gparted.sourceforge.net/") to do that.

---

### Post by el_colombiano on 2006-10-21
thanks 
:-D

---

### Post by Sef on 2006-10-21
You're welcome.  Please post any other questions that you have.

---

### Post by gn2 on 2006-10-21
With that much RAM you could easily use VMWare Server free edition or Parallels Desktop and run Ubuntu in a Virtual machine?

[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

[http://www.parallels.com/](http://www.parallels.com/)

---

### Post by el_colombiano on 2006-10-21
hey i ran into a problom with runing the live cd and having the linux programs on a partion on the hard drive the partion i want to use cant be mounted or something.  here is a sreenshot of it [http://i102.photobucket.com/albums/m120/El_colombianoboi/Screenshot.png](http://i102.photobucket.com/albums/m120/El_colombianoboi/Screenshot.png)

once again i like to say thanks for helping me.:)

---

### Post by gn2 on 2006-10-21
> **Sef said:**
> You're welcome.  Please post any other questions that you have.

Looking at your signature, I see that the plural of virus is viruses.

Could the collective noun be a "Windows" of viruses?

---

### Post by Herman on 2006-10-21
> hey i ran into a problom with runing the live cd and having the linux programs on a partion on the hard drive the partion i want to use cant be mounted or something. here is a sreenshot of it [http://i102.photobucket.com/albums/m...Screenshot.png]("http://i102.photobucket.com/albums/m120/El_colombianoboi/Screenshot.png") That isn't the way we mount our partitions, here is a link to a page that will explain to you how you can do that, [Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm")
I hope that will be of some help to you,

I was looking for a how-to I saw somewhere about how to create a persistent /home for the Ubuntu LiveCD, similar to the way we can make a 'persistent home' on the hard disk for Knoppix. 
Is that what you are trying to do? 

The closest one I have found so far is this one, for a USB pen drive,  [https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)

   Regards, Herman :D

---

