---
title: "[SOLVED] Removing Vista, but backing it up..."
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-08-10
Can I copy all the windows files and save them to another disk, delete the partition, then if I want create a new partition, put the files on it, and boot into it?

Is it that simple?

Can I create a vista filesystem withing linux to do this.

---

### Post by SOULRiDER on 2007-08-10
Sure, just mount  the hard drive with vista, and copy the files to some other partition :)

First make a directory where you want to mount the drive
```
sudo mkdir <location>
```
then, mount the drive, you will have to know the drive letter and the partition number though
```
sudo mount /dev/<drive> <location>
```

Good luck, if you need further assistance dont hesitate to ask either here or ove IRC.

EDIT: I just re-read your post. I highly doubt you will be able to boot to it.. but you can always try =/

---

### Post by tdrusk on 2007-08-11
> **SOULRiDER said:**
> Sure, just mount  the hard drive with vista, and copy the files to some other partition :)

First make a directory where you want to mount the drive
```
sudo mkdir <location>
```
then, mount the drive, you will have to know the drive letter and the partition number though
```
sudo mount /dev/<drive> <location>
```

Good luck, if you need further assistance dont hesitate to ask either here or ove IRC.

EDIT: I just re-read your post. I highly doubt you will be able to boot to it.. but you can always try =/
Well basically I just want to save Vista since I paid for it.

---

### Post by vexorian on 2007-08-11
Did vista come in an OEM? then you don't really have to backup vista, you can just reinstall it later if you want. Unless you want your files in which it is good to keep the partition, isn't it?

---

### Post by tdrusk on 2007-08-11
> **vexorian said:**
> Did vista come in an OEM? then you don't really have to backup vista, you can just reinstall it later if you want. Unless you want your files in which it is good to keep the partition, isn't it?

It came preloaded on my computer without a reinstall cd.

---

### Post by bluemarvel on 2007-08-11
> **fuzzyhair said:**
> Well basically I just want to save Vista since I paid for it.

If Vista came as an OEM install, you'll probably have to boot into Vista and then run the "make backup install disks" shortcut buried somewhere in your Start menu. Most computer manufacturers don't include install disks.

I don't believe you can reliably backup a Windows installation by simply copying files and then hope to restore it unless you make a disk image and do it that way.

---

### Post by tdrusk on 2007-08-11
> **bluemarvel said:**
> If Vista came as an OEM install, you'll probably have to boot into Vista and then run the "make backup install disks" shortcut buried somewhere in your Start menu. Most computer manufacturers don't include install disks.

I don't believe you can reliably backup a Windows installation by simply copying files and then hope to restore it unless you make a disk image and do it that way.

How can I do that?

---

### Post by por100pre1 on 2007-08-11
> **fuzzyhair said:**
> It came preloaded on my computer without a reinstall cd.

Didn't it come with a partition with the Vista install files neither? :-k

---

### Post by tdrusk on 2007-08-11
> **por100pre1 said:**
> Didn't it come with a partition with the Vista install files neither? :-k
I have an acer partition with my windows and program files on it.

---

### Post by por100pre1 on 2007-08-11
> **fuzzyhair said:**
> I have an acer partition with my windows and program files on it.

I mean a partition with the Vista install program, like an OEM Vista disk but in a partition. I think you should contact your PC maker about the possibility of getting an OEM disk...  :-k

---

### Post by tdrusk on 2007-08-11
> **por100pre1 said:**
> I mean a partition with the Vista install program, like an OEM Vista disk but in a partition. I think you should contact your PC maker about the possibility of getting an OEM disk...  :-k

That would be nice.

It came with an "upgrade" cd... that's it.

---

### Post by armandh on 2007-08-11
back in the 98se days you could move to a larger drive and boot with 
xcopy C:\ F:\ /h/e/c/k/r but I have not been too successfull with it since.
xp came with the files and/or settings copy utility, but one still had to install the operating system and apps. [safer as all the corupt junk from generations of upgrading stayed behind] better,  one could try to put  all the files of a xp partition on to a dos 32 bit partition that ubuntu can access easly [let's call it old home] then if [if that works]you delete the xp partition you still have all the files.

---

### Post by por100pre1 on 2007-08-11
> **fuzzyhair said:**
> That would be nice.

It came with an "upgrade" cd... that's it.

So they give you an "upgrade" CD, but they don't give you an install CD. Not my idea of good service. You should definitely contact your PC maker and tell them to mail you an install CD. Be sure to complaint, you already paid a Vista license when you got your PC.

---

### Post by Sbarton on 2007-08-11
Just sometimes it's worth taking the existing drive out (therefore keeping Vista intact) and installing another drive and installingUbuntu.
regards

---

### Post by bluemarvel on 2007-08-11
> **fuzzyhair said:**
> That would be nice.

It came with an "upgrade" cd... that's it.

My HP Pavilion laptop came with a Vista "upgrade" CD but it's actually a full blown version of Vista. I can do a clean install with it. Is your "upgrade" CD for Vista alone or is it an upgrade utility for all the bundled software?

I have a hunch that if you needed to you could install Vista right from that CD, but you might want to test it to make sure first.

As far as making backups of your pre-installed Windows software, many Windows computers with OEM stuff have a "Create Backup DVDs" shortcut in their start menu that allows them to make DVD backups of the software on their "hidden" partition.  Have you looked through your start menu on your Windows installation?

---

### Post by tdrusk on 2007-08-11
> **bluemarvel said:**
> My HP Pavilion laptop came with a Vista "upgrade" CD but it's actually a full blown version of Vista. I can do a clean install with it. Is your "upgrade" CD for Vista alone or is it an upgrade utility for all the bundled software?

I have a hunch that if you needed to you could install Vista right from that CD, but you might want to test it to make sure first.

As far as making backups of your pre-installed Windows software, many Windows computers with OEM stuff have a "Create Backup DVDs" shortcut in their start menu that allows them to make DVD backups of the software on their "hidden" partition.  Have you looked through your start menu on your Windows installation?

When I boot up there is a recovery partition (10gb) that I just ran. It reinstalled Vista. Now that I know that I have that partition, what can I do with that and my current situation.

I really just want to have Ubuntu on my computer with no other partitions. Any suggestions?

---

### Post by bluemarvel on 2007-08-11
> **fuzzyhair said:**
> When I boot up there is a recovery partition (10gb) that I just ran. It reinstalled Vista. Now that I know that I have that partition, what can I do with that and my current situation.

I really just want to have Ubuntu on my computer with no other partitions. Any suggestions?

In your new Vista installation there should be a program to backup that 10GB recovery partition, then you can wipe it out and install Ubuntu.

---

### Post by bluemarvel on 2007-08-11
> **fuzzyhair said:**
> When I boot up there is a recovery partition (10gb) that I just ran. It reinstalled Vista. Now that I know that I have that partition, what can I do with that and my current situation.

I really just want to have Ubuntu on my computer with no other partitions. Any suggestions?

I found this on the Acer website:

Create backup
              English
               You can create and save backup images to hard disk, CD or DVD.
               1    Boot to Windows XP
               2    Press <Alt> + <F10> to open the Acer eRecovery Management utility.
3                   Enter the password to proceed. The default password is six zeros.
4                   In the Acer eRecovery Management window, select Recovery settings and
                    click Next.
               5    In the Recovery settings window, select Backup snapshot image and
                    click Next.
               6    Select the backup method.
                    a     Use Backup to HDD to store the backup disk image on drive D:.
                    b     Backup to optical device to store the backup image on CD or DVD.
               7    After choosing the backup method, click Next.
               Follow the instructions on screen to complete the process.

---

### Post by Anzan on 2007-08-11
As I understand it, backing up a Vista installation requires 3 DVDs or 14 CDs.

I just had the drive pulled out and fresh drive put in and put the Vista drive on a shelf in case it's ever needed. Where it has sat untouched for months.

---

### Post by tdrusk on 2007-08-11
> **bluemarvel said:**
> I found this on the Acer website:

Create backup
              English
               You can create and save backup images to hard disk, CD or DVD.
               1    Boot to Windows XP
               2    Press <Alt> + <F10> to open the Acer eRecovery Management utility.
3                   Enter the password to proceed. The default password is six zeros.
4                   In the Acer eRecovery Management window, select Recovery settings and
                    click Next.
               5    In the Recovery settings window, select Backup snapshot image and
                    click Next.
               6    Select the backup method.
                    a     Use Backup to HDD to store the backup disk image on drive D:.
                    b     Backup to optical device to store the backup image on CD or DVD.
               7    After choosing the backup method, click Next.
               Follow the instructions on screen to complete the process.

awesome thank you!

---

