---
title: "Can't boot Ubuntu because it can't mount hda"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by dennisgodderie on 2006-02-16
Situation:

C (windows) NTFS
D (data) NTFS
E (data2) NTFS
F (Linux) Ext3 (for ubuntu)
G (Swap)

That was what I had, and I managed to install Ubuntu perfectly. But then I started trying to mound my D and E partition in Ubuntu. Didn't worked very well. But that's not the problem. I now have merged my D en E partition to 1 D partition. But in my fstab in Ubuntu, the E partition is still mounted. Now if I try to boot Ubuntu it displays a message in console-style that he can't mount my E (hda6 I think) and therefor can't boot ubuntu.

What can I do about it? I know am using Ubuntu Live CD, thought to edit my fstab file, but I can't see the partition of Ubuntu (not the one from the cd, that one I do can see)

Somebody a suggestion?

---

### Post by psusi on 2006-02-16
1) What do you mean you merged the partitions?  How?  Maybe you blew up your ubuntu partition in the process.  

2) Failing to mount the ntfs partition would not prevent you from booting.  What exctly does the error say?

3) Boot from a livecd and see what sudo fdisk -l /dev/hda says.

---

### Post by arctic on 2006-02-16
Grab a full fledged live CD like Knoppix, boot it, go into root user mode and mount the ubuntu partition. Edit the /etc/fstab file and your menu.lst file and hope for the best. But I think you will run into other problems later due to the symlinks in /dev...

---

### Post by psusi on 2006-02-16
[QUOTE=arctic]Grab a full fledged live CD like Knoppix, boot it, go into root user mode and mount the ubuntu partition. Edit the /etc/fstab file and your menu.lst file and hope for the best. But I think you will run into other problems later due to the symlinks in /dev...[/QUOTE]


There is no need for Knoppix, the Ubuntu livecd works just fine.  

Also /dev is a ram filesystem anyhow, everything in it is created on the fly as the system boots up or as you (un)plug hardware, so you won't run into any sort of problem like that.  

Also telling someone to blindly edit their fstab and hope for the best isn't really very good advice.  He obviously doesn't know exactly how to edit it, and he should not have to either.  I fear something more serious has gone wrong, so more information is needed to diagnose the problem.

---

### Post by dennisgodderie on 2006-02-16
1. Merging partition = from 2 partitions (D and E) going to one big partition (D).
I didn't deleted the ubuntu partition, I'm sure about that.

2. Well I chose Ubuntu in the grub loader, and then I get the message that he can't boot because he can't mount hda6 (previously my E-drive (data2)). Don't know the exact error, but I'm sure that's for 90% what it says.

3. If i boot from live cd and typ sudo fdisk -l it only shows 2 partitions. 1 NTFS and one Win98 from the external hard disk that I plugged in.


I'm going to try to boot again from the live cd. Could you say what commands I need to use to mount my ubuntu partition when using the live cd?

su
mount /dev/hda (number that correspondes with my ubuntu partition)

or should I do something more?

---

### Post by psusi on 2006-02-16
I assume you used partition magic or something to do this?

It sounds like the partition number of the root filesystem changed so you will need to update grub.  

If you boot the machine and press escape when grub starts to load, then press e to edit the menu option.  Highlight the line that starts with kernel and press e to edit that.  It should have root=/dev/hda6 on it.  Change the 6 to a 5 and hit enter, then b to boot.  

If that works, then edit your /boot/grub/menu.lst file and find a line like this:

# kopt=root=/dev/hda6 and again replace the 6 with 5.  Save the file and run sudo update-grub, and you should be fine.

---

### Post by WolfJay_83 on 2006-02-16
If you have further trouble, the following may help from your live cd...

It's likely that when you "merged" your two drives, the numbers (ex hda1, hda2, etc) have shifted down.  You need to update your fstab and grub to match.

first to check your partition numbers type,
```
sudo cfdisk
```

This will give you a partition manager that will list the hda#s for each partition.  If you see that your hda#s are different then exit out of that and update the numbers in fstab and grub by typing.  
```
sudo nano /etc/fstab
sudo nano /boot/grub/menu.lst
sudo nano /etc/mtab
```

in each file, you just need to change the numbers for the partitions to reflect the change in your cfdisk.  Note the grub menu.lst is long, but go to the end and work back, the important line will start with "kernel /boot". Anything above "## End Default Options##" in the file are of no importance.

Hope this helps

---

