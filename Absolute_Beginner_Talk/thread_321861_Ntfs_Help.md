---
title: "Ntfs Help??"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by felipriscilla on 2006-12-19
okay so this is what I did:

1. Partioned my NTFS harddrive using the ubuntu live disk to allow installation of ubuntu. works great.

2. Try to select Windows Media Center from boot screen, it brings up the text "starting up.." and then does aboslutely nothing.

3. Ran the recovery for Windows MCE (HP computer so the backup is on a partition on the harddrive)

4. Tryed to run Windows Media Center, still nothing

Now I could always do a hard recovery which would delete every partion on the harddrive and reinstall the system but I have some files I want to retrieve from my NTFS partion (the original MCE install). The partion is dev/sda1, all I want to do is copy some files on to my usb fat32 harddrive. The problem is that I am new to linux and can't figure out how to navigate thru the partion. I read the help file on using NTFS in ubuntu and it tell me to go to administrator and go to "Disks" and click here and there to allow me to view files but there is no "Disks" option. I've tried to navigate thru the file manager like you do in a windows enviroment but once i click on the partion it tells me it doesn't know what to do with it.

---

### Post by annda on 2006-12-19
did you navigate to your windows partition as /dev/sda1 in the filesystem? if the partition is mounted, access it through /media/sda1 or /media/some_name if it has a name.

you should be able to copy anything you want after that. good luck!

---

### Post by felipriscilla on 2006-12-19
hmmm.. didn't think of looking under media. i'll try once i get home from work. thanks for the respond.

---

### Post by gh0st on 2006-12-19
Have you tried going to your /mnt folder to see if there is anything mounted in the subfolders there?? Thats the default location for mounting drives. For instance, I have a windows partition that is mounted automatically as win_c under the folder /mnt/win_c

Ubuntu should have set this up for you when you installed it. the name may not be the same as mine it could be anything but there should be something in the /mnt folder, it's in the root folder of the system.

Let me know if there's anything in that location, maybe Ubuntu can't read NTFS because of an error with the driver. I use NTFS-3G which allows me to read and write on NTFS. There is a good walktrough of how to install NTFS-3G on Ubuntu on the Lunapark website. Here's the link [http://lunapark6.com/?p=1710](http://lunapark6.com/?p=1710)

Hopefully som eof that helps a bit :)

If you need any help with NTFS-3G let me know, I've had to get it working on a few friends machines already.

---

