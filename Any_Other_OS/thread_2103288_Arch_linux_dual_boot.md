---
title: "Arch linux dual boot"
date: 2013-01-09
forum: Any Other OS
---

### Post by f1ndingwalden on 2013-01-09
I am curious about dipping my toes into arch linux and was wondering if a dual boot with a computer already running ubuntu would be possible, and if so how I would go about doing this. 
Thanks!

---

### Post by pissedoffdude on 2013-01-09
That's not a problem.  Grub will be able to boot into arch and Ubuntu.  Some common options include
(1) Installing arch, then installing grub onto your current hard drive's master boot record and auto-detecting your ubuntu install via the os-prober package (Check out [https://wiki.archlinux.org/index.php/GRUB2]("https://wiki.archlinux.org/index.php/GRUB2")
(2) Installing arch, then installing grub on the arch partition and running "sudo update-grub" in ubuntu

I recommend you check out the beginner's guide on the archwiki and using Gparted before you boot into arch's install environment, as the command line partitioning tools can be a bit intimidating.  Good luck!

---

### Post by f1ndingwalden on 2013-01-10
Thanks, Im stoked this works... 
Also if I have a 750gb hard drive, how much would you recommend I partion arch to be?
And one last question because I dont know much about dual boot, would I be able to access my files (like music and docs saved in my home folder) in arch, or are they completely separated?

---

### Post by viperdvman on 2013-01-10
Arch can run perfectly fine on a partition as little as 8 or 10GB pretty easily. But if you have the space to space, use a 40GB partition or more for Arch, which will give you plenty of room to add however many apps you want, however many desktop environments you want, run Virtual Machines, etc.

I'm currently running Arch as more of a toy on a 15GB partition myself (Kubuntu is my primary, Bodhi is my secondary)

---

### Post by fantab on 2013-01-12
> **f1ndingwalden said:**
> I am curious about dipping my toes into arch linux and was wondering if a dual boot with a computer already running ubuntu would be possible, and if so how I would go about doing this. 
Thanks!

Just don't install the bootloader GRUB when you install Arch. I dual boot with Arch and I don't.

Just  update-grub from ubuntu after installing Arch and remember to mount the Arch partition before you run update-grub in Ubuntu.

---

### Post by f1ndingwalden on 2013-01-13
Would any of this be possible after ubuntu is already installed? On gparted it says I have to unmount the current partion, but wont that prevent me from using the computer?
Sorry if this sounds dumb, this is my first experience with partioning.

---

### Post by Bucky Ball on 2013-01-13
You're best off partitioning from the LiveCD. That way all partitions can be unmounted. If you're looking for resize partitions, they need to be unmounted. Also, say if you want to manipulate sda5, all partitions with lower numbers than that need to be unmounted.

You can't resize the / partition which Ubuntu is installed on while it is mounted, as you have discovered.

---

### Post by viperdvman on 2013-01-13
> **fantab said:**
> Just don't install the bootloader GRUB when you install Arch. I dual boot with Arch and I don't.

Just  update-grub from ubuntu after installing Arch and remember to mount the Arch partition before you run update-grub in Ubuntu.

I remember installing grub on my Arch, but I installed it to the same partition as my Arch install, and not to the MBR.

I do this with every Linux because I dual-boot with Windows 7 and prefer to use the Windows Bootloader. And then I use EasyBCD to add the entries for each Linux that I'm running. It's worked for me every time, and has worked for Arch.

---

### Post by trent.josephsen on 2013-01-13
I actually prefer syslinux over grub, but I'd second fantab's advice. All you need is some free space to put Arch in; you don't need to install a second bootloader.

---

### Post by kiyop on 2013-01-13
> **f1ndingwalden said:**
> And one last question because I dont know much about dual boot, would I be able to access my files (like music and docs saved in my home folder) in arch, or are they completely separated?
Yes, you can access your files in ubuntu home folder ("directory") /home/YOUR_USER_NAME from arch, if you correctly mount the ubuntu parttiion from arch.
```
man mount
```As for the place to which grub should be installed, read [http://ubuntuforums.org/showthread.php?p=11975894#post11975894](http://ubuntuforums.org/showthread.php?p=11975894#post11975894) No.1).
I suggest you installing grub2 or grub legacy to the PBR of the / (root) or /boot partition of each linux distribution, ubuntu and arch, and installing chainloader to the MBR, although I prefer my tool. ;)

---

### Post by trent.josephsen on 2013-01-14
> **kiyop said:**
> As for the place to which grub should be installed, read [http://ubuntuforums.org/showthread.php?p=11975894#post11975894](http://ubuntuforums.org/showthread.php?p=11975894#post11975894) No.1).

Arch does in-place kernel updates without changing the filename, so that is a non-issue. The boot loader doesn't need to be reconfigured when a new kernel is installed.

---

### Post by Megaptera on 2013-01-14
> **f1ndingwalden said:**
> ... would I be able to access my files (like music and docs saved in my home folder) in arch, or are they completely separated?

If you leave your existing home partition as it currently is when you install Arch it should be accessible - don't format it when working through patitioning options at install.

But do take full back-up of your important docs,pics,vids etc - to external media - just in case!! :p

---

### Post by f1ndingwalden on 2013-01-14
Thanks for all the advice guys, one last question about partioning though.. 
If I were to partion off my existing os from a live cd, would that have any effect on the files and programs in there, or would it just cut down space?

---

### Post by f1ndingwalden on 2013-01-14
Also, could I acces and partion even though my home folder is encrypted?

---

### Post by linuxcoffeelover on 2013-01-14
I just installed arch in VirtualBox and I'm really considering formatting and installing arch as my main OS. Kde is beautiful and pacman is great to use. I'm going to play with it more and I think anyone how loves linux will love using arch.

maybe after I great after I master arch one day I'll Install gentoo.

---

### Post by trent.josephsen on 2013-01-14
As long as you use a tool that recognizes Linux partitions such as GParted, you run almost no risk of losing data. That's not to say you shouldn't back up your data just in case, but if you don't have the storage space, you don't run a significant risk of data loss by simply shrinking the partition containing your Ubuntu installation. (Leave a few GB of wiggle room, though; don't shrink it as small as you can.)

The process will be a little more complicated than just GParted if you have an LVM setup or if one or more of the existing partitions are encrypted with LUKS or Truecrypt or something like that. (Ubuntu's "Encrypted Home" feature does not encrypt the entire partition, so that wouldn't pose a problem.) But in the simple case where your Ubuntu OS lives on a plain primary or logical partition, yeah, just resize it with GParted and reboot to make sure everything still works before installing Arch onto the newly created free space.

As for the other question, since you say your "home folder" is encrypted, I'm going to guess that means you used Ubuntu's encrypted home feature and did not create an encrypted partition to mount /home on. In which case I don't have personal experience but I can reassure you that the tools used to implement that feature are also available for Arch (community/ecryptfs-utils). It may take some configuration to get it to work right, though.

---

### Post by kiyop on 2013-01-16
> **trent.josephsen said:**
> Arch does in-place kernel updates without changing the filename, so that is a non-issue. The boot loader doesn't need to be reconfigured when a new kernel is installed.
Thanks for the above post of yours. :)

---

### Post by oscarivera9 on 2013-01-22
> **fantab said:**
> Just don't install the bootloader GRUB when you install Arch. I dual boot with Arch and I don't.

Just  update-grub from ubuntu after installing Arch and remember to mount the Arch partition before you run update-grub in Ubuntu.

Everytime I install any other OS I opt for the option of no bootloader and then I boot into ubuntu and sudo update-grub just like you suggest.

Also, if you're thinking about installing Arch, I recommend doing it in VirtualBox first.  I just got done doing that and it was quite an experience!  I learned a lot from it and I'm doing it virtually so that I can get a better grip for how to do it on a real hard drive.

---

### Post by f1ndingwalden on 2013-01-22
Thats a really great idea, and I think thats what ill do today, especially considering the amount of trouble I have had setting it up. I believe that this is a much smarter alternative to someone thats never used it before.

---

### Post by oscarivera9 on 2013-01-22
> **f1ndingwalden said:**
> Thats a really great idea, and I think thats what ill do today, especially considering the amount of trouble I have had setting it up. I believe that this is a much smarter alternative to someone thats never used it before.

It took me a long time doing it yesterday and I made it through most of it with little hiccups but encountered problems when I got to the package management selection.  I'm not completely happy with my results so I will probably reinstall it again this week.  That's the beauty of VirtualBox, that you can play around with it until you get it right and at the same time you can keep using your main OS as if you were just running another program -- because you are.

Make sure to follow the Arch wiki as it does a great job at guiding you through almost all of it.

[https://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](https://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

---

### Post by bfmetcalf on 2013-01-22
The installation guide is good, but I would recommend the beginners guide.  I have been running Arch for a few years now and still go to the beginners guide over the installation guide when I install it fresh.

---

### Post by offgridguy on 2013-01-22
> **f1ndingwalden said:**
> Thanks, Im stoked this works... 
Also if I have a 750gb hard drive, how much would you recommend I partion arch to be?
And one last question because I dont know much about dual boot, would I be able to access my files (like music and docs saved in my home folder) in arch, or are they completely separated?
Sorry i see this has already been answered.

---

