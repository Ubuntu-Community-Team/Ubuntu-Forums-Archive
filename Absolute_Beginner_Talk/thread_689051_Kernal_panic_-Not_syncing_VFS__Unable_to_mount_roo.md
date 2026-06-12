---
title: "Kernal panic -Not syncing :VFS : Unable to mount root fs on unknown-block (0,0)"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by dcrawl on 2008-02-06
I recently did a clean install of Ubuntu 7.10 onto my old laptop. I had everything up and running for about a week and then today, after booting into windows XP, restarting and trying to load Ubuntu I get the error

 Kernal panic -Not syncing :VFS : Unable to mount root fs on unknown-block (0,0)

The other threads that talk about this error have been no help to me as I did not upgrade to 7.10 from 7.04 and can't use that kernal to boot. I can, however, boot from a live CD. I have no idea where to go from here other than a reinstall. Any help would be greatly appreciated.

---

### Post by szymon_g on 2008-02-06
is it showing when you choose 'ordinary' kernel or also when you chose 'recovery mode' :?

---

### Post by dcrawl on 2008-02-06
It shows when I choose both my normal boot option and (recovery mode). I'm pretty sure that it isn't a hard drive error because i can still boot to my windows partition.

---

### Post by dcrawl on 2008-02-06
Any help anyone? I'll wait until I'm out of work for any other suggestions before I format and reinstall 7.10.

---

### Post by doug-M on 2008-02-08
I just had a very similar problem, same error message. Turns out for me the /boot/initrd.img-2.6.22-14-generic file was 0 bytes.

So what I did was this:
Boot using a live CD, Ubunto 7.10 but Knoppix or others should work as well.
Open a terminal window (Applications > Accesories > Terminal)

sudo mkdir /mnt/hd
  (this is just creating a directory to use as a mount point)
sudo mount /dev/sda1 /mnt/hd
  (this mounts my unbootable hard drive)

(I used System > Administration > Partition Editor, to find which was my boot partition, in my case /dev/sda1)

Then I looked at the files in /mnt/hd/boot and noticed initrd.img-2.6.22-14-generic was 0 bytes but the file initrd.img-2.6.22-14-generic.bak was 6.9MB

ls -las /mnt/hd/boot

So I did
sudo cp initrd.img-2.6.22-14-generic initrd.img-2.6.22-14-generic_backup
  (just to be safe)
sudo cp initrd.img-2.6.22-14-generic.bak initrd.img-2.6.22-14-generic

Then rebooted and everything was fine.

Note: You can also check your /mnt/hd/boot/grub/menu.lst to make sure that the kernel and initrd parameters point to real files e.g. in my case initrd is:
 initrd		/boot/initrd.img-2.6.22-14-generic
Also in menu.lst the root parameter should be pointing to your bootable partition, the root= on the kernel parameter might list a UUID which should match an entry in /mnt/hd/etc/fstab, or you can try it with the name such as /dev/sda3.

---

### Post by wareagle on 2008-02-10
Had the same problem after installing updates using Adept on Kubuntu 7.10.  It said one of the updates failed.  Not sure which one though; none were kernel updates.  And as soon as I clicked OK, Adept crashed.

But I noticed my kernel image file (initrd.img-2.6.22-13-generic) was 256K.  Restoring the backup Kubuntu had made fixed the problem.

=D>

---

### Post by dcrawl on 2008-02-18
I eventually found out that this happens to mainly HP/Compaq laptops after a Kernal update that is only a  proposed update in your Software sources. If you have an HP/Compaq I do not suggest checking this box. I do not know how to fix this problem but if you reformat and avoid these updates everything runs just fine.

---

### Post by portach king on 2008-02-18
EDIT: I FOUND A FIX - 100% Credit goes of MightyMos ([http://ubuntuforums.org/showpost.php?p=4314372&postcount=4](http://ubuntuforums.org/showpost.php?p=4314372&postcount=4))

On My Live CD
I Opened Terminal and entered
```
sudo mount /dev/hda1 /mnt
sudo chroot /mnt /bin/sh
sudo update-initramfs -u
```

Your Hard Disk name may vary, I suggest you open Partition Editor (System>Administration>)  on the Live CD and use it to check the name of yours (and not to create any new partitions :) ). As you can see in my case it was hda1. Yours may be sda1 or other variants.

That worked for me. Simple and I sincerely hope it helps others. I also hope that my advise is sound, those who know Linux better can correct me if it isn't.

---

### Post by cre8ivgil on 2008-03-02
After a few frustrating days I found the above post by doug-M, followed the instructions and rebooted. Worked perfect! Thanks a lot for this useful post doug-M.

---

### Post by sajasio on 2008-03-06
can someone explain a simpler solution i have no training with computers i pretty much self taught so i dont know the technical terms. i have a dell inspron 6000 w/ a celron intel procesor if that is helpful at all

---

### Post by doug-M on 2008-03-09
In my post above are you able to do any parts of it?

Perhaps we could help walk you through it?

---

### Post by squizzi on 2008-03-22
I logged in just to give you a gigantic appreciative THANK YOU! Doug-M!

After about 5 hours of frustration and troubleshooting, a bunch of reboots and LiveCD experiences (including the LiveCD not even booting!) I got my computer to boot thanks to your nicely written guide.  And I especially thank you for that, seeing as I am new to linux, following your lines of code was no problem at all.

I believe my kernel became corrupted form me closing down startupmanager prematurely ... I was looking forward to seeing my updated uSplash, sadly, I got a kernel panic..

Thanks again.

---

