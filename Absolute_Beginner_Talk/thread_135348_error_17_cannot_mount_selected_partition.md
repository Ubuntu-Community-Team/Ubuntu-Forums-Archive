---
title: "error 17: cannot mount selected partition"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by sallam on 2006-02-23
my ubuntu doesn't start!

Last time, as I recall, I mounted my other partitions that has my files back when I used windows. I have 6 partitions, one of them is used exclusively for ubuntu.

My installation of ubuntu is the standard, out of the box type. Dont ask me what am I using, I probably wont be able to answer, but I did not alter any standard thing.

what do I do now?

btw, I notice that there are 6 boot options, not 3 like it used to be.
I tried all of them, save mode and all, and nothing works. All return the same error 17 message. Only 'Windows XP pro' option is working now..

---

### Post by andrewsawyer on 2006-02-24
If you can get access to the Linux partition, either using a LiveCD or some software for Windows, it would be good if you could show us your /boot/grub/menu.lst and /etc/fstab files.

Then we might be able to get it sorted for you.

---

### Post by Craig Caldwell on 2006-02-24
[QUOTE=vnbuddy2002]Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
..... 

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.[/QUOTE]

This is the method i used to get grub working again.
make sure that you remount your / , /home , swap partitions.
scroll up to the mount in the partition option and hit enter.
you will then chose / or /home from a list.
after going through your / , /home and swap partitions save your changes by scrolling all the way to the way down to the bottom of the page for the save option. It wasn't obvious to me that there were more options when you scroll down
to the bottom.
After installing grub get into the shell and "reboot" 
Do not continue with the install.
If things start happening that you don't want remember to use Ctrl -c to stop.

this is a simple solution that took me many hours of scouring the forums to get and then follow correctly.


error15 
error 15
error17
error 17
can't fix grub
can't boot
fallen and can't get up
reinstall grub
fix grub
I'm going to smash this thing
bootloader
can't mount
ubuntu won't boot
xp won't boot
I'm going to use my boot

Not sure if this will help bring people to this post for a great grub fix but it would have made my day easier if I'd found this fix sooner.

---

### Post by sallam on 2006-02-24
thanks for trying to help me.
I think a fresh install would be easier for me.
I'll probably wait for the next ubuntu version.

How can I remove the boot screen and return my computer to start with Windows directly as before?

---

### Post by Kurt` on 2006-02-24
Launch into Windows, and from a command prompt type:

> fdisk /mbr

To overwrite your master boot record with the default Windows one.

---

### Post by sallam on 2006-02-24
> Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Administrator>fdisk /mbr
'fdisk' is not recognized as an internal or external command,
operable program or batch file.

C:\Documents and Settings\Administrator>
I typed it exactly as you advised me, but it didnt work.

---

### Post by sallam on 2006-02-26
anyone please?

---

### Post by sallam on 2006-02-26
Craig Caldwell,

I finally took your advise and did as you explained above. It was easier than I thought, many thanks. I'm finally able to go to my ubuntu, from which I'm typing now! Its been almost a month, phew..!

Only the '/boot' part in the instructions was confusing, as I have only 2 partitions, one for / and one for swap. The root / partition is bootable itself.

It turned out that my '/' partition was mounted as /media. Obviosly its my mistake, as I recall the last time I was trying to mount my other windows partitions.

Many thanks everyone for your great help.

---

### Post by tonibaumann on 2007-01-31
Hello
I had a hack a lot of problems the last 3 days installing xubuntu trying all different schemes according to books and forum research error 15/17 or stage1.5. Please wait
It seemed odd I used as well different hard drives during the procedure no luck.
I more and more got the idea that this might be a bios problem.
I have to mention this is a pretty old system AMD k62 550 motherboard ca. 1997
The strange thing was that I originally made an Ubuntu install from the live CD on a 3, 2 GB Disk just let it install it self not changing anything and it went fine.
Thinking about all this in retrospective, where again I got a "stage1.5. Please wait" screen blinking away after an installation with boot partition, root partition, home and swap partition to get around this 8 GB issue.
So I tried to find a solution in the Bios, in STANDART CMOS SETUP where you can change the hard disk mode between auto/normal/large/and LBA.
I changed from STANDART to LARGE and suddenly all problems vanished everything works.
AUTO might work as well haven't tried yet.
I just wanted to share my experience here that sometimes I might help checking if the BIOS might be cause before one tries solutions on comandline.
Hope that is some help to anybody out there
Toni

---

