---
title: "Can't Move/Edit/Make Partitions - Please Help!!"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by CREEPING DEATH on 2006-06-13
Home-built system, Athlon 2200XP+, 256MB, 60GB WD HD as primary and 40GB (actually about 38GB) Maxtor HD as secondary, both using NTFS.  The 60GB was blank but used when I got it, I installed XP on it about 3 years ago.  The 40GB was salved from my old HP after the Athlon fried.  ALL I have been able to do is remone the 40GB's 4.5-Gig recovery partition, the reformatted it from NTFS to ext3 to FAT32.  XP sees it as G.  I could not enlarge the 33.5GB partition to 38GB after removing the 4.5GB partition.
Every time I try the installer, I get an error message that it couldn't create enough space for an install.  I have used the installer and GParted on the LiveCD, and attempted the "Alternate CD" as well.  NOTHING works!
What I want to is install Ubuntu on a new 10GB partition on the 60GB drive, then make another partition on the 60GB and start transferring all my files from NTFS to FAT32.  Three partitions on the 60GB:  10-20 for XP, 5-10 for Ubuntu (including swap and possibly /home partition), remainder in FAT32 for shared files.  One partition on the 40GB.
I had the same problem installing Xubuntu on my cousin's desktop, I ended up reformatting the entire drive.  That is NOT an option for me on the computer, I have too many files and such I need to save (about 50-60 GB).
I don't know why I'm having such a hard time, I installed Ubuntu on a Dell Latitude C610 laptop, resizing the W2KPro to 10GB on the 30GB drive.  It went easy, works nearly flawlessly (has a lock-up issue, I think it's the video driver issue discussed elsewhere), and I love it!  It will hopefully be wireless soon, I have to get a card first.

Thanks,
Jeff

---

### Post by morequarky on 2006-06-13
Let me get this straight.  This is what you want?

hda0 20GB XP
hda1 10GB Ubuntu
hda2 30GB Fat32

hdb0 36 - 38GB

Can you post a screenshot of your current partitions and drive?

---

### Post by CREEPING DEATH on 2006-06-13
[QUOTE=morequarky]Let me get this straight.  This is what you want?

hda0 20GB XP
hda1 10GB Ubuntu
hda2 30GB Fat32

hdb0 36 - 38GB

Can you post a screenshot of your current partitions and drive?[/QUOTE]

Yes, sounds about right.  I can't edit partitions at all.  I downloaded Knoppix and burned a LiveCD to use QTParted, but I can't figure out how to use it.  All it told me was that the drive had "at least 14 bad sectors."  Isn't QTParted on one of the Ubuntu dirtros?  Kubuntu maybe?
I'll reboot intu Kubuntu and see what I can do as far as screen shots.

Thanks,
Jeff

---

### Post by CREEPING DEATH on 2006-06-13
Here are the screen shots.  What am I doing wrong?  I'm going to try QTParted on Kubuntu.

Thanks,
Jeff

---

### Post by morequarky on 2006-06-14
Ok.  I don't know why your computer is saying hda-1 or hdb-1.

How are the drives wired in the case?  I am guessing hdb is SLAVE of hda.  Make sure the drive is set to slave on the motherboard AND the back of the drive.  Which drive do you want to be the main drive and which one do you want to be the slave?  Maybe you need to change them around and change some "jumpers" in the computer.  Unsure, I would check.

You have two "active" partitions.  Both are NTFS windows.  Are you dual booting windows?  XP and XP Pro?  Don't reformat. Find out which NTFS partition boots by default and make the other Windows partition so it doesn't say active.  Windows boot loader doesn't want two active NTFS I would bet.  You need GRUB, linux' bootloader, if you aren't already using it.

Make sure your NTFS partition doesn't have more data then you think in it.  Can't make a 15GB partition into a 10GB partition if you have 12GB of data in it.

Make sure of your setup.  I don't think it is a Ubuntu problem.

---

