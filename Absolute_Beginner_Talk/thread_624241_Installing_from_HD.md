---
title: "Installing from HD"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Paradoxfox93 on 2007-11-26
I'm basically wanting to know if I can partition off 800MB of my HD for space for an ISO or just the files of the boot CD and then use that to boot my computer to the 'liveCD' environment.  I'm trying to do this because I find myself re-installing frequently while trying to get new versions of Ubuntu running correctly.  Moreover I typically like to reinstall about once a month at the least anyway. Since I knwo I'm going to be reinstalling about 4-5times a day till I get Gutsy running (After that: 64bit!).

Is this even possible?

---

### Post by jfinkels on 2007-11-27
> **Paradoxfox93 said:**
> I'm basically wanting to know if I can partition off 800MB of my HD for space for an ISO or just the files of the boot CD and then use that to boot my computer to the 'liveCD' environment.
I don't believe so...wouldn't that just be an installation?
> I'm trying to do this because I find myself re-installing frequently while trying to get new versions of Ubuntu running correctly.  Moreover I typically like to reinstall about once a month at the least anyway. Since I knwo I'm going to be reinstalling about 4-5times a day till I get Gutsy running (After that: 64bit!).

Is this even possible?
You can use PartImage to take a snapshot of a partition once you have your installation working the way you want it to work, and then just restore that whenever you want a working installation. [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by Paradoxfox93 on 2007-11-29
> **jfinkels said:**
> I don't believe so...wouldn't that just be an installation?

No.  Actually based on what I read somewhere else I think I can just mount the .ISO itself.  I'm not sure how to do that.  I tried to follow the guys instructions for mounting the starcraft .ISO but I never got it to work...or starcraft for the matter.  Still, I'd need a separate partition to do what I'm talking about so I could preform the installation without mounting the HD to install to.  It seem it would just be too complicated anyway so I've really scratched the idea.
> 
You can use PartImage to take a snapshot of a partition once you have your installation working the way you want it to work, and then just restore that whenever you want a working installation. [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Thanks, that will be helpful if an when I do get linux working the way I way to.  unfortunately it doesn't operate the way I'd like just yet.  Even the basics I can only make operational in 32bit Feisty.  I've tried 32bit gutsy to no avail.  It crashes on me every time I try to connect wirelessly with WEP security; although, it does not crash when connecting to an open network.  Making my network open is not an option however.  I actually stubled across that one quite randomly.

---

### Post by bodhi.zazen on 2007-11-29
Well, with that many re-installations, you could consider virtualization

You can boot the iso with qemu, VirtualBox, or VMWare. IMO the latter two are faster.

virtualization will allow you to take snapshots as well.

---

### Post by jfinkels on 2007-11-30
> **Paradoxfox93 said:**
> No.  Actually based on what I read somewhere else I think I can just mount the .ISO itself.
To mount a .iso, first make a mountpoint (a directory to which you want to mount the image), and then do the following:```
sudo mount -o loop -t iso9660 */path/to/file.iso* */path/to/mountpoint*
```
where */path/to/file.iso* is the path to the .iso file you wish to mount, and */path/to/mountpoint* is the path to the directory in which you want to mount the image.

I was able to get Starcraft to work successfully once. Have you looked at [http://appdb.winehq.org/objectManager.php?sClass=application&iId=72](http://appdb.winehq.org/objectManager.php?sClass=application&iId=72) ?

It seems unlikely that there would be a method to do what you suggest; can you point me to a link which contains such a method?
> **bodhi.zazen said:**
> Well, with that many re-installations, you could consider virtualization

You can boot the iso with qemu, VirtualBox, or VMWare. IMO the latter two are faster.

virtualization will allow you to take snapshots as well.
+1, I agree.

---

### Post by bodhi.zazen on 2007-11-30
> **jfinkels said:**
> It seems unlikely that there would be a method to do what you suggest; can you point me to a link which contains such a method?

I think something like this :

[http://pendrivelinux.com/](http://pendrivelinux.com/)

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

Also some distros can do this as well, I am most familiar with Wolvix. On Wolvix it is called a "Frugal install" where the iso is on a hard drive and one boots the iso from there.

[http://wiki.wolvix.org/HardDriveInstall](http://wiki.wolvix.org/HardDriveInstall)

(see the second section "Frugal Install")

Wolvix also allows you to save your changes : [http://wiki.wolvix.org/WolvixIntro](http://wiki.wolvix.org/WolvixIntro)

I am sure there are other distro's that do this, dyne:bolic for example, it is just I am most familiar with Wolvix.

---

### Post by jfinkels on 2007-11-30
> **bodhi.zazen said:**
> I think something like this :

[http://pendrivelinux.com/](http://pendrivelinux.com/)


I am aware of pendrivelinux.com...however, I thought it was just a traditional install + booting from a USB drive. Apparently I'm wrong :D

---

### Post by bodhi.zazen on 2007-11-30
> **jfinkels said:**
> I am aware of pendrivelinux.com...however, I thought it was just a traditional install + booting from a USB drive. Apparently I'm wrong :D

LOL, yea, I know, that is what I originally thought too ...

---

### Post by Paradoxfox93 on 2007-12-04
Yeah, but battle.net doesn't work. I've actually got my computer dual booted with the OEM vista CD that came with my laptop. (Ugh :P)  Grub loader is freakin' awesome though.  It handles Dual bootin' like a pro.  I used to try to dual boot 98/98 with different configuations (One for work and one for gaming) and it was always giving me crap.  I'm going to see if I can't part up my drive and get one of those progs to work. Thanks for the tips everyone.

Pendrive will be interesting to try when I pick up a 2GB MicroSD for my sansa C240 (great little piece that doubles as a USB flash drive with it's own MicroSD slot, which one can put Linux/Rockbox  on).  That'll definately be something I'll do to try to sell (as in convince her to use, not as in make a profit) Ubuntu to my girlfriend who just bought a new computer (HP...yuck...LOL)

---

