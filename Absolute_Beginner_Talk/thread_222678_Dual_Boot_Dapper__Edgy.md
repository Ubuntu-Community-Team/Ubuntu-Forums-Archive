---
title: "Dual Boot Dapper / Edgy"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by jethro10 on 2006-07-25
Hi,
This I hope qualifies for the beginners forum?
I have a problem now I think.

I have Dapper on my PC,and had left a blank partition that I just put Edgy on.
And its working fine.

However the Grub loader seems to be the one on the Edgy partition, but it has nicely listed the boot options for the Dapper partition. So at the moment I can run anything, including the Dapper partition and it older kernels that are listed.

so this I think is my problem. As Edgy is the 'master' (is that the right term?) grub loader, IF I get a major update for dapper with a new kernel, the grub updated will be the dapper, not the edgy one, so it will not be in my grub loader that is now the default one and i wont be able to choose it to load.

So my basic question is How to move control back to Dapper Grub, then how would I move this back to Edgy grup in 4 months time when edgy is finalised. I gather then I can delete the Dapper partition and use it for the new Ubuntu 7 release!

PS : I have my /home on a seperate partition and use a different username for each release I log on to so I dont screw up hidden files that relate to each release. Is this the right thing to do?

wow.

Thanks to anyone with enough stamina to read all of this.

Jeff

---

### Post by moma on 2006-07-25
> **jethro10 said:**
> Hi,
so this I think is my problem. As Edgy is the 'master' (is that the right term?) grub loader, IF I get a major update for dapper with a new kernel, the grub updated will be the dapper, not the edgy one, so it will not be in my grub loader that is now the default one and i wont be able to choose it to load. Jeff

Yes, that's right. Edgy has installed its own boot-menu and made the MBR (and bootloader) to boot by using it. Edgy is in charge.

You can give control back to Dapper quite easily. Do this

**1) Boot up using the Dapper Live CD. **
Edgy's or another Live CD will do as well.

[ You could easily boot into Edgy and do all the work from there, but it's better to use a LiveCD for disk maintenance tasks.]

**2) You have booted into LiveCD.**
Start terminal program (gnome-terminal) from Applications -> >Accessories menu and issue these commands:

BTW: You haven't told about the disks, so I assume here that 
/dev/sda1 = Dapper Drake partition
/dev/sda2 = Edgy Eft partition

Mount Dapper's partition to /media
$ [COLOR="Green"]sudo mount /dev/sda1 /media [/COLOR]

Make chroot jail on /media 
$ [COLOR="Green"]sudo chroot /media[/COLOR] 

You should now see a root prompt (#).
Re-install grub on /dev/sda (Replace MBR on the MAIN boot disk.
That is the disk your PC's BIOS will boot from).
# [COLOR="Green"]grub-install /dev/sda[/COLOR]

Alternative command: You can also achieve the same result witout using chroot jail. /media has to be mounted as explained.
$ [COLOR="YellowGreen"]sudo grub-install --root-directory=/media /dev/sda[/COLOR]

(Of course, replace /dev/sda1 and /dev/sda with correct disk in your case)

**3) Reboot**
# reboot
---------------------------------

**4) Take the latest copy of menu.lst**

As you know, Edgy has the latest (newest) copy of /boot/grub/menu.lst.

You can replace Dapper's /boot/grub/menu.lst with Edgy's or just copy over the new menu-lines so you can dual-boot between Dapper and Edgy.

$ [COLOR="Green"]sudo gedit /boot/grub/menu.lst [/COLOR]

// moma
   [http://www.futuredesktop.net/ubuntu6.06.html]("http://www.futuredesktop.net/ubuntu6.06.html")


ps. If you have further questions, copy and paste output of these commands  w/ your message.

$ sudo fdisk -l

Take the essential lines only (no # comments)
$ cat /boot/grub/menu.lst

---

### Post by jethro10 on 2006-07-25
Thanks Man !!

At least I had correctly diagnosed my problem.

Thanks

J

---

### Post by edude on 2006-10-03
[QUOTE=moma;1298526]

[ You could easily boot into Edgy and do all the work from there, but it's better to use a LiveCD for disk maintenance tasks.]

I used the Alternate cd and i cannot use the LiveCD. Could you please tell me how can i do this stuff from Edgy. 

Many thanks in advance.

---

### Post by justin whitaker on 2006-10-03
> **edude said:**
> [QUOTE=moma;1298526]

[ You could easily boot into Edgy and do all the work from there, but it's better to use a LiveCD for disk maintenance tasks.]

I used the Alternate cd and i cannot use the LiveCD. Could you please tell me how can i do this stuff from Edgy. 

Many thanks in advance.

From Edgy, using the text install, click through the prompts until you get to the partitioning stage. 

Select Manual Partitioning. 

Resize the existing Dapper install to make room for Edgy.

Create a new partition in the freed space. Make note of the partition name.

Install Edgy to the new partition. Check it against the partition you made. It would suck to overwrite both.

You can use the same SWAP partition.

Continue through the installation. 

At grub install, it should prompt you for all other OSes on the system. If you have XP and Dapper, both will show.

Click OK.

Reboot.

Cross Fingers.

YMMV. :mrgreen:

---

### Post by edude on 2006-10-03
Thanks Justin. Actually i am currently running Edgy in one partition and i am going to install Dapper in another one, and i think of sharing the same HOME, which is placed in another partition, but with different user names for each of both releases. So i would like to solve the question of being governed by the Edgy grub and the problems it will entail when i decide to update the kernel under my dapper install.

---

### Post by justin whitaker on 2006-10-03
> **edude said:**
> Thanks Justin. Actually i am currently running Edgy in one partition and i am going to install Dapper in another one, and i think of sharing the same HOME, which is placed in another partition, but with different user names for each of both releases. So i would like to solve the question of being governed by the Edgy grub and the problems it will entail when i decide to update the kernel under my dapper install.

The steps are not any different. Just make sure you do not touch the /Home drive. You might need to edit fstab to automount the /Home directory, but updating dapper should not affect either the home directory, the edgy install, or grub.

---

### Post by Xappe on 2006-10-03
Here's a little suggestion:

I just let Dapper and Edgy have their own grub menu. I had dapper on there from start, so I use the grub in my bootpartition as the main grub (installed to mbr), and installed the edgy grub on the edgy rootpartition (not mbr, this can be achieved by using the alterate install cd).

Then I just chainloaded edgy's grub with a static entry in dapper's /boot/grub/menu.lst

By doing this I get the kernel updates for dapper on my main grub menu, and the ones for edgy on the chainloaded one...

---

### Post by edude on 2006-10-10
> **Xappe said:**
> Here's a little suggestion:

I just let Dapper and Edgy have their own grub menu. I had dapper on there from start, so I use the grub in my bootpartition as the main grub (installed to mbr), and installed the edgy grub on the edgy rootpartition (not mbr, this can be achieved by using the alterate install cd).

Then I just chainloaded edgy's grub with a static entry in dapper's /boot/grub/menu.lst

By doing this I get the kernel updates for dapper on my main grub menu, and the ones for edgy on the chainloaded one...

I got it! 
First installed Edgy in one partition and home in another one. I left two other partitions free just in case and in one of them installed Dapper. Then i mounted the partition for home (used in Edgy) and moved Dapper's home directory there. I assume it is important to create different user names for Edgy and for Dapper, as i did to avoid problems with the user's configuration in each release.

Thanks for the help.

---

### Post by mrastas on 2006-10-20
Hello,

I am trying to install edgy nexto dapper on same laptop, but i did not have enough courage to go trough the manual partition. So i tried to search google and this forum for some help and this topic was the closest thing i could find.

Everywhere i found articles about installing ubuntu with XP and dualboot, but i did not find any guides howto install edgy after dapper... WITHOUT loosing dapper root and home partitions.

1. question is it possible to install with DESKTOP-CD or is alternate CD required?

2. If Desktop-CD is ok, then how to use gparted to get it right. Currently i have hda5 as home, hda6 as root and hda7 as swap. I have unnallocated space left on the same hard drive about 13 Gb.

I played around with gparted, but as i said i did not have the courage to go trough with it without any confirmation from a GURU. :D 

Thanks ahead for any comments/help.

Marko

---

### Post by Xappe on 2006-10-20
> Hello,

I am trying to install edgy nexto dapper on same laptop, but i did not have enough courage to go trough the manual partition. So i tried to search google and this forum for some help and this topic was the closest thing i could find.

Everywhere i found articles about installing ubuntu with XP and dualboot, but i did not find any guides howto install edgy after dapper... WITHOUT loosing dapper root and home partitions.

1. question is it possible to install with DESKTOP-CD or is alternate CD required?

2. If Desktop-CD is ok, then how to use gparted to get it right. Currently i have hda5 as home, hda6 as root and hda7 as swap. I have unnallocated space left on the same hard drive about 13 Gb.

I played around with gparted, but as i said i did not have the courage to go trough with it without any confirmation from a GURU.

Thanks ahead for any comments/help.

Marko



1. It's indeed possible to install and create a dual boot with the desktop cd, but I don't think you'll be able to choose where to install grub. So you'll probably end up with a system where you have to manually update the grub menu when new kernels are installed (for one of the distributions).

As I said in the above post; if you choose to install edgy grub to the edgy root partition and just chainload to that one from dapper's grub, you can let the systems update their own grub menus. This can be achieved with the alternate cd and some easy editing of the dapper /boot/grub/menu.lst

2.You could use the allocated space for the edgy root partition (maybe a bit too much...don't think you need all that space) and use the same /home partition as dapper but with another user name perhaps? :)

---

### Post by edude on 2006-10-22
It may help with Xappe point 2 this url:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

