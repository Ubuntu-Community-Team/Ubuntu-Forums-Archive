---
title: "What do I do next?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by marxman47 on 2007-09-29
Hi.  I've just installed a new HDD on my computer and intend to put Ubuntu on it.  I have been running Ubuntu for a while now on a dual-boot with XP and I think it would be better to completely separate the two systems.

Having done the easy bit, actually bolting the new disk in place and attaching the wires, I am faced with carrying out a real installation.

I have found out, by reading other posts in the forum, how to remove Ubuntu from my old HDD, how to reclaim the space for XP and how to restore the MBR from my XP install disk - all OK so far.

I wonder if it is necessary, or just a good (or bad) idea to remove the SATA wire from the disk when I place the Ubuntu CD in the CDROM drive, so that Ubuntu 'sees' only one disk, the new, clean one with no XP?  Will it install GRUB to the new disk?  (I don't see how it could do otherwise, but I'm asking for my hand to be held a bit.)

On starting my computer, if I tap the F8 key it takes me to a 'Boot Menu' where I can select a first boot device, which should, if my thinking isn't completely woolly, allow me to start with either Ubuntu or XP, depending on which HDD I choose.

Any guidance, thoughts, moral support, prayers etc would be most welcome :).

Thanks in advance from a superannuated newbie.

marxman47

---

### Post by Happy_Man on 2007-09-29
Yep, that's just about the safest way to do it. Remove the SATA wire, GRUB will install to the Ubuntu disk, you choose at startup, if disk 1, Windows, if disk 2, GRUB, and then Ubuntu. Should work. Good luck.

---

### Post by CaptainInsaneO on 2007-09-29
I'm running Ubuntu on one harddrive and WinXP on another and have never had a problem with grub. You just install grub to whichever physical disc comes first. If you goober it up you can always run fixmbr on your windows disc and/or reinstall grub.

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by marxman47 on 2007-09-29
A big thank you to both Happy_Man and CaptainInsane0  - you have been a great help - tomorrow I shall do the deed!  Carpe diem and all that! :KS

Greta forum, by the way - loads of help in the stuff already posted, I've just discovered!

Best regards,

marxman47

---

### Post by CaptainInsaneO on 2007-10-06
So how did it go? :guitar:

---

### Post by marxman47 on 2007-10-07
It hasn't gone at all yet, thanks for asking!  Family business and a busted loo have taken up all my time - until today - I'm just about to do it.

Thanks for the advice and the good wishes - if all goes according to plan I'll post again later - and with any luck I'll be able to say 'Fine'.

Best regards, marxman.

---

### Post by marxman47 on 2007-10-07
Well - it's done, but not without its difficulties!

I tried a manual install including a large home partition after starting with the CD and all seemed well until the installation was about 80% done, when a warning appeared that the HDD was at 100% full.

I started again and this time chickened out to a Guided Install of the Entire Disk and that went very well; I connected to the internet and got the updates and will shortly be plugging in the old Windows Disk too (a brief message about GRUB appears on start-up from the new HDD).

I think I may have an idea where I went wrong; for the home partition I wanted to create, the first time around, I typed in** /home** where I think it should have been **/ home**.  Is it possible for me to use the Live disk later to create a home partition using gparted?  I think it ought to be possible, but I'm only guessing, to be honest :(.

Now I have to remove my old Ubuntu installation from my Windows disk and restore the MBR on it.  Any guidance you could offer with this would be most welcome - I feel as if I'm within an ace of having the system I want, but I just need this help over the final stages.  Can I remove the Ubuntu partitions using Disk Manger in Windows and reclaim the space as a new Windows partition?  I've read about fixmbr somewhere, but I can't seem to find it.

Apologies once more for being such a pain, but thanks in advance to the great bunch of guys and gals on the forums who have helped me so much already.

Very best regards, marxman47.

---

### Post by dptxp on 2007-10-07
If I were you I would reinstall with both HDD connected.
No need to format partitions, mount drives, and edit Grub later.
You do All in one go.

---

### Post by marxman47 on 2007-10-07
Hello dptxp and thanks for your reply.  If I can just tell you...

With both HDDs plugged in, I can now tap F8 when starting up and choose which HDD to boot from.  I am currently in Windows, mainly because it's got all my Bookmarks and I wanted to see if it worked - it does.

I don't really relish the idea of going through it all again quite so soon, however!  I'm frankly amazed that it's come this far so well and I'm not the sort to push his luck.

What I want to do now is to remove the Ubuntu partitions from my 'Windows' Disk and remove the GRUB on the same disk, replacing it with the Windows mbr.  If you have any suggestions as to how to do this, they would be absolute joy!

I could, if absolutely necessary, learn to live with the GRUB on the Windows Disk, but I'd rather get rid of it entirely.

Again, thanks for your help.

Best regards, marxman47.

---

### Post by dptxp on 2007-10-07
A reinstallation will take about one hour. You shall be able to resize, format and mount as you please and put Grub where you like (last step in installation, click on 'advanced' at bottom right, easy to miss).

You will be able to choose you OS after boot, Ubuntu shall be default but you can change it.

Make a nice / home, and keep a spare ext3 partition of say 6-12 GB to try other distros later, you can always use that for data.

If you do not want Windows to write to / partition, use FAT32 for the data partitions that both Windows and Linux can read. If you enable ext3 in Windows it will r/w that too.

A few partitions always help, you can move data from one to other, sort of defragmentation. 

Do not be scared to reinstall, it shall set everything in order. You have done it once, do it again.
One hour job.

---

### Post by marxman47 on 2007-10-07
UBUNTU 7.0.4 Installation - Sunday October 6 2007

I have a Western Digital HDD, which came with my (quite new) PC and a Maxtor HDD I installed the other day.  They are both 160 GB.

I placed the Ubuntu Desktop CD in the tray and shut down the PC.

I disconnected the SATA cable to the Western Digital HDD, the one with dual-booted XP and Ubuntu.

I switched on the PC and booted into the Live Ubuntu Desktop.  I selected INSTALL and the installation began.  I opted for a Manual Installation.

I set 20 GB as the root partition, 2 GB as the swap partition and the remainder I intended to be a /home partition.  All seemed to go well until the installation was about 80% complete, when a message appeared saying that the HDD was 100% full and everything stopped.  I switched off the PC and restarted, this time choosing the option of Guided - Use Entire Disk.  This completed, giving me 2 partitions, one "/" and one "swap".

I shut down the PC and reconnected the Western Digital HDD and restarted again.  Tapping the F8 key brought up the Boot Menu and I selected the Western Digital HDD and this brought up the GRUB menu I was familiar with.  I selected Windows XP Home and was taken to the log-in page.  On shutting down and accidentally restarting, the PC booted into the new Ubuntu Installation with no trouble.

I would like to remove the existing dual-boot Ubuntu installation from this disk, leaving the new disk clear for Linux only.  I understand that the Ubuntu partitions can be formatted and the space reallocated to XP.  I also believe that by using the XP Install disk I can restore the MBR and lose GRUB from the Western Digital HDD.  

If my reasoning is clear, then I would need to reinstall Ubuntu; I need to isolate the Maxtor (Ubuntu) disk by disconnecting the Western Digital SATA cable and reinstalling Ubuntu on the Maxtor, taking more care over the selection and sizing of mount points, "/", "swap" and "/home".  Perhaps a little time with a calculator might be of value!  Then I can reconnect the Western Digital and all will be well with the world :KS!

Again, I feel so close to achieving the set-up I would really like to have, one in which I can select which Hard Disk and thereby which OS to use at start-up.  Any further advice, or suggestions as to what went wrong in the first place, would be a God-send.  I have watched the screencast by Alan Pope and I still can't see where I made my error - I know now that it wasn't "/home" as that is what he used in his tutorial.

In a word, HELP!

Best regards, marxman47.

---

### Post by marxman47 on 2007-10-08
Hello again and thank you all for the advice you have offered me in the last couple of days.

Today I have reinstalled Ubuntu on my Maxtor HDD (twice - the reason for that is too embarrassing to pass on while I'm sober!) and have removed the dual-boot from my Western Digital **and **restored the Win XP MBR. :guitar:

So - when I start up now, I can get the Boot Menu by tapping the F8 key and choose which disk and which OS I want to use - just what I always wanted, to quote Mari Wilson!

Again, many thanks and if anyone new is having similar problems, I've got a sheaf of notes that might help you out!

Very best regards, marxman47.

---

