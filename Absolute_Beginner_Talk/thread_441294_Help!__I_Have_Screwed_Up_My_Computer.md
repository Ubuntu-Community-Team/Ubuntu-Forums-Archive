---
title: "Help!  I Have Screwed Up My Computer"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by cygnis1 on 2007-05-12
Help!!!  I tried to install Ubuntu7.10  (dual boot with XP) last evening and made a complete mess of my computer.  I have lost my Master Boot program and can no longer boot to windows.  I can use the Ubuntu live cd to access my computer, but Ubuntu is not installed, at least it does not boot on startup.  I now have eight partitions, there were four when I started.  They are /dev/sda 1,2,3,5,6,7,8, and 9.  /dev/sda 1 and 2 are the windows partitions (c and d).  /dev/sda 3 is an extended partition of 160G, and I think it is locked (lock icon).  /dev/sda 5 says linux-swap of 90G lba.  It is also locked.  /dev/sda6 is ntfs and is one of my original partitions.  It is back up and is readable in linux.  /dev/sda7 is an fat 32 partition of  14G.  /dev/sda8 is and ext3 partition of 2G and is listed as Boot.  /dev/sda9 is listed as linux-swap with 164G.  /dev/sda3,5,and 9 all appear to be locked.  Can I unlock them using gparted?  I used the assisted partitioning last evening when the manual partitioning tool wouldn't work.  Is there some way I can undo this mess?  Can I recover windows?  Or do I need to forget the windows and install Ubuntu as primary and only OS?
Thanks,
Cygnis1

---

### Post by Happy_Man on 2007-05-12
Oh no, Windows is happily still on your hard drive, so is Ubuntu. The problem is that you have gone and not installed GRUB, which lets you choose which OS to boot. Reinstall Ubuntu, using that exact setup, and when you get to the final step, where it asks "are you ok with this?" check to make sure that there is a line somewhere that says "grub, (0,0)". If you don't, GRUB won't get installed. Also, check your disc for errors by using the handy-dandy "check your disk for erros" option on inital LiveCD boot. Hope this helps!

---

### Post by [S|G] on 2007-05-12
Ok, to begin with, you need to unmount the partitions once you have the livecd running. Open a terminal and type this:
```
sudo umount /dev/sda5
```
That should unlock /dev/sda5. Repeat the process for sda9. The extended partition should be unlocked once you unmounted all logical partitions inside it. Now start gparted and delete every partition you don't need (probably everything but the windows partitions, sda1 and sda2). Be VERY careful not to delete your windows partitions.

After you're done, you should have your disk with lots of free space and your original windows partitions. You can now try to install linux again. By the end you'll probably have grub working.

There is also a way to restore window's boot manager, and that would be booting the windows cd-rom, entering the recovery console and using the command "fixmbr".

---

### Post by cygnis1 on 2007-05-12
I tried the recovery disk (windows) and it would not work.  When I was finishing up the install I never got the message is everything ok.    So I have to go throught the installation process again?  And this will restore xp?
Thanks

---

### Post by [S|G] on 2007-05-12
When you finish installing grub will search your disks for operational systems and include them on the boot menu. So you should have the option of booting into XP back.

---

### Post by cygnis1 on 2007-05-12
I just looked at gparted and it won't allow me to delete the locked partitions.  That option is shaded, and not available.

---

### Post by cygnis1 on 2007-05-12
How do I install Grub, and where do I install it?
Thanks

---

### Post by siralphred on 2007-05-12
this is how u reinstall GRUB [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by [S|G] on 2007-05-12
EDIT: Nvm, follow the instructions above :)

---

### Post by cygnis1 on 2007-05-12
I have read the article, and my question(s) is this.  Do I install Grub on /dev/sda8 which contains the boot file, or on /dev/sda5 which is listed as linux-swap?  I do not have a /root partition.  And can I install Grub on a partition that is locked?
Thanks,
Cygnis1

---

### Post by [S|G] on 2007-05-12
Usually you install it on the first partition of the first harddrive (in your case, /dev/sda1)

---

### Post by cygnis1 on 2007-05-13
I have tried unmounting /dev/sda5, typing in : sudo umount /dev/sda5   when I hit return I get the line : umount: /dev/sda5: not mounted .  I did the same for /dev/sda9 and when I looked at gparted, all partitions but /dev/sda2 were locked.  I have another rescue disk with gparted on it and it looks like I can delete partitons with it.  Would that be ok?

Thanks,
Cygnis1

---

### Post by Happy_Man on 2007-05-13
Yeah, use something like an Edgy LiveCD. Feisty randomly locks stuff...did the same with my swap partition.

---

### Post by cygnis1 on 2007-05-13
I was working with gparted on the linux recovery cd, but could not move the partitions.  Would a Partition Magic 8 rescue disk help?  That was how I originally repartitioned my hd.
Thanks,
Cygnis1

---

