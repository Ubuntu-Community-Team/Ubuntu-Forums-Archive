---
title: "Locked Out --Emergency"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by skier on 2007-08-20
I was working on installing thinkfinger and I commented out the file:

/etc/pam.d/common-auth

I can not log into my account anymore. I rebooted and my username is being rejected.   How can I get back in?

---

### Post by kebes on 2007-08-20
Boot into a LiveCD, mount the hard-drive, and edit the file(s) you changed back to their proper state. Then reboot into your normal OS.

---

### Post by skier on 2007-08-20
Hi I pulled up the file but it is "read only"????

---

### Post by amazingtaters on 2007-08-20
You've got sudo it to get root privileges.

---

### Post by skier on 2007-08-20
> **amazingtaters said:**
> You've got sudo it to get root privileges.

I understand that.  Can someone explain how to do this from the command line?  Looking at the GUI interface I can click on 'disk' and find the file.  When I try and find it from the command line, I do not know how to get to the hard drive

---

### Post by RonDutt on 2007-08-20
Simple and easy, open up terminal and type:
sudo gedit

gedit (GUI) will open with root privs so you can modify the file by just clicking on the 'disk' and browsing to it.

Without knowing your hard drive configuration I can't tell you where the file may reside so you can edit it via command line, but it seems you were just looking for a way to edit the file with root privs.

---

### Post by skier on 2007-08-20
> **RonDutt said:**
> Simple and easy, open up terminal and type:
sudo gedit

gedit (GUI) will open with root privs so you can modify the file by just clicking on the 'disk' and browsing to it.

Without knowing your hard drive configuration I can't tell you where the file may reside so you can edit it via command line, but it seems you were just looking for a way to edit the file with root privs.

No.  This is the problem that I am having.  This opens the clean file from the cd,  not the file I edited on my harddrive.

When I look at my command line it is :
ubuntu@ubuntu:~$

When running properly my command line is usually:
me@me:~$

---

### Post by Shazaam on 2007-08-20
As kebes said you have to mount your hard drive while in the livecd then you can edit the file.

Running the livecd=
Open terminal, type in (without the quotes) "sudo fdisk -l" (small L) This will give you your hard drive info (example= /dev/hda1)
Type in "sudo mount /dev/DRIVE /mnt (substitute your hardrive info for DRIVE, this will mount the drive, there is a space before /mnt)
Type in "gksudo nautilus" (this will open nautilus with ROOT privileges BE CAREFULL!)
Browse to the file you need to edit and open it. Uncomment what you changed, save it and close nautilus.
Open terminal type in "sudo umount /dev/DRIVE
Done.

---

### Post by skier on 2007-08-20
my hard drive is /dev/sda1

when i enter:
sudo mount /dev/sda1 /mnt

I get the message:
according to mtab, /dev/sda1 /mnt is already mounted on /mnt

I enter:
gksudo nautilus

nautilus opens.  I do not see my harddrive.  I see:

root
Desktop
File System

File System contains the clean file from the disk.  Root contains nothing

---

### Post by nowshining on 2007-08-20
go on the live CD to the following

filesystem - home - your username to get to your username files, incase you need to backup firest

filesystem should have the files on your hard disk..

edit: go to filesystem media and then your harddisk

i just remembered

---

### Post by skier on 2007-08-20
> **nowshining said:**
> go on the live CD to the following

filesystem - home - your username to get to your username files, incase you need to backup firest

filesystem should have the files on your hard disk..

NO.  People, do you understand that I am LOCKED OUT and my home folder does not show up???

> edit: go to filesystem media and then your harddisk

i just remembered

Please explain.

---

### Post by skier on 2007-08-20
Solved

---

### Post by Shazaam on 2007-08-20
How?

---

### Post by nowshining on 2007-08-20
glad you got it fixed and I meant with LIVE cd of course. lolz.. :)

---

