---
title: "Can I make another Bootable hard drive"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-02-27
Hi all

What i would like to do is to backup my internal hard drive to the USB hard drive so i could take the internal hard drive out and replace it with the backup hard drive that is bootable in the computer.

The USB hard drive is NOT a thumb drive or Flash card it is a real Toshiba 20GB drive.

After looking at backup threads most are for ISO files to CD. or from CD to hard drive.

I would like to copy complete internal hard drive to external hard drive via USB and end up with a bootable hard drive.

the external hard drive currently has a Ubuntu somewhat working system that could be erased.

The external hard drive is 20 GB

So i think i would have lots of room because the current internal hard drive is only 6 GB

I don't want to boot from a CD or thumb drive i just want a bootable copy of my internal drive.

Is it possible to do this and if yes what would i need to do.

Thanks

---

### Post by dvarsam on 2006-02-27
Hello.

I would suggest that you read this article:

136195		- Looking for a "Norton Ghost 2003" for Linux

I had similar needs.

I am still experimenting to find which solution is more suitable for me.

Read the limitations/requirements of each solution VERY carefully though.

Example:
One solution requires that BOTH Hard Drives MUST have the same size...
I do NOT know if you could create a Partition with the size you need though, to overcome that problem...

...and by the way, if you find a solution, keep us posted!

Because I still have NOT yet managed to find a "Full Backup Solution" either.

---

### Post by kent41 on 2006-02-27
After searching the web and Forum post for hours I had no idea how hard it is in LINUX to make a backup copy of the Ubuntu system, partitions and files, I don't know if it is a security problem and making a disk to disk copy is to risky to have this capability. 
On the surface a disk to disk image seems so simple, but I guess it is a major major undertaking. From what I have been reading what make it so difficult is having different partitions. Can I assume that it is a bad idea to want a backup copy of a complete hard drive.  I guess I must succumb to the Idea that if I have a hard disk failure I must go thru the hours of rebuilding my system from scratch or make incremental backups which I was trying to stay away from. 
I just wanted to replace my hard drive and continue. From what I see on the Forum others would also like to have the capability of a full hard drive backup. Foolish me I thought a disk just stored bits and bytes and you could copy them one at a time until you ran out of bits. It would be a great service to all if someone with the knowledge and programing skills could write a scrip to make a disk backup.

---

### Post by bertpatt on 2006-02-27
Use g4u.
Iv'e used it to copy a whole hard drive over to a blank hard drive.
I connected up the drive I had copied to and it booted up OK.
The only limitation was that because the hard drive I was copying was 60 gig and the other one I was coping to was 80 gig, the size of the 80 gig drive showed 60 gig.
The program is a bit slow but it works.
I tried Nortons Ghost 2003 but it didn't boot.

---

### Post by kent41 on 2006-02-27
[QUOTE=bertpatt]Use g4u.
Iv'e used it to copy a whole hard drive over to a blank hard drive.
I connected up the drive I had copied to and it booted up OK.
The only limitation was that because the hard drive I was copying was 60 gig and the other one I was coping to was 80 gig, the size of the 80 gig drive showed 60 gig.
The program is a bit slow but it works.
I tried Nortons Ghost 2003 but it didn't boot.[/QUOTE]
bertpatt
Thanks
 Do I need to format the destination drive ? The destination drive is connected via USB

---

### Post by steve.horsley on 2006-02-27
I think you can probably do this with (check the drive letters):
sudo dd if=/dev/hda of=/dev/sda
to just do a pure copy. This will NOT leave you with a bootable USB disk because the GRUB loader will be trying to load the internal drive, but it may well work if you install the USB disk in place of the 6G drive.

Take a copy of the USB disk partition table first so that you can put the right partition table back if your experiment fails.

And take everything I take as specuilation - I have never tried this and could be horribly, horribly wrong. 

Of course, if you're only taking a copy so that you can restore a backup to another drive later, you could use DD to copy to a FILE on the USB drive. You could use a live CD to copy from USB back to a replacement drive.

---

### Post by kent41 on 2006-02-27
Steve.horsley

Thanks we tried but the following commands and the results were not good.

```
sudo dd if=/dev/hda of=/dev/sda
```

The files on the USB hard drive were garble-gook and they were not folders but files.
it looks like we need  a **-r** switch for the dd command.

I have re-formatted the USB hard drive so we are back to square 1.

Thanks again

---

### Post by dvarsam on 2006-02-27
If you can wait a couple of days & you are NOT in a hurry, I will post a Tutorial on how to do it with a TAR command.

But you will have to wait...

Right now I have to go to sleep.

However, give us your feedback, because I am also concerned on this...

---

### Post by kent41 on 2006-02-27
[QUOTE=dvarsam]If you can wait a couple of days & you are NOT in a hurry, I will post a Tutorial on how to do it with a TAR command.

But you will have to wait...

Right now I have to go to sleep.

However, give us your feedback, because I am also concerned on this...[/QUOTE]

Yes I can wait because I think there are a number of users would like to do this.

Thanks for your time

---

