---
title: "What can I do with LiveCD?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Howard Kaikow on 2007-05-12
Prior to installing 7.04 on a windoze PC, i'd like to play with LiveCD.

What can I run from the Ubuntu LiveCD?

I ASSuME that I can verify what devices can be seen, accessed, etc.

What about dialing up using PPP, or browsing with a web browser?

Anything else that does not require writing to a drive?

---

### Post by Tux Aubrey on 2007-05-12
Its been a while since I used a Live CD (I have updated my systems online since Dapper) but I know that one of the things that really impressed me was that it detected my broadband connection and I was web browsing immediately.  That was huge "wow factor" for me back then as I'd been expecting the same difficulties I'd had getting it to work on Windows.

I'm not really sure, but I think you can also mount drives and do a bit of tweaking.  Just plug everything you own into the computer and boot.  You can't break anything so just play!

Welcome and good luck.

---

### Post by dpar on 2007-05-12
I think you can pretty well do anything that you can do with a perminant install except perminantly install changes to the live cd.

---

### Post by Howard Kaikow on 2007-05-12
THanx.

I'll try to:

1. Dial in using PPP.
2. Test my scanner.
3. See if I can mount all my drives.
4. Connect to another PC. Other PC has Win 95, so might that be an obstacle.
5. What about trying, say, Firefox and Thunderbird. Files have to be recorded to do this?

---

### Post by the.phantom on 2007-05-12
you might have troubles with the dialup !!!!!!!!

do some looking around the forum and you will get answers for most though


if you use a winmodem it wil need a linux driver
i got dialup to work easy with 6.06, and took a bit of work on 6.10 with some changes they made and at that point i gave up and figured i better join society and went high speed , and haven't installed fiesty yet

---

### Post by Howard Kaikow on 2007-05-12
> **the.phantom said:**
> you might have troubles with the dialup !!!!!!!!

do some looking around the forum and you will get answers for most though


if you use a winmodem it wil need a linux driver
i got dialup to work easy with 6.06, and took a bit of work on 6.10 with some changes they made and at that point i gave up and figured i better join society and went high speed , and haven't installed fiesty yet

No winmodem here.

Internal Courier.

---

### Post by 3rdalbum on 2007-05-12
Don't worry about whether a particular task requires writing to a hard disk. Ubuntu treats your RAM like a hard disk, so you can basically make any changes as long as they don't require a restart to take effect. Remember, once you shut down or restart, those changes you've made are lost unless you put the files onto an external disk of some sort.

---

### Post by Howard Kaikow on 2007-05-12
> **3rdalbum said:**
> Don't worry about whether a particular task requires writing to a hard disk. Ubuntu treats your RAM like a hard disk, so you can basically make any changes as long as they don't require a restart to take effect. Remember, once you shut down or restart, those changes you've made are lost unless you put the files onto an external disk of some sort.


good.

So I should be able to browse with Firefox and send email from Thunderbird.

---

### Post by the.phantom on 2007-05-12
yes you will be able to work firefox ( don't know if t-bird is default mail in fiesty or not?)

changes you make to the firefox and such won't be saved as won't write to the cd ;-D

i used a external modem on the serial port when i was on dialup and was no problem

---

### Post by jerrylamos on 2007-05-12
On Dapper 6.06 and Edgy 6.10 and a number of other Linux Distros you can have a "persistent" mode where CD Live files, changes, and even package installs are saved on a USB pen drive.  You can even take the CD Live and USB to another computer and continue what you were doing with your files, settings, and installed packages.  

Some distros like Puppy allow you to save your work etc. on a file on XP so you have everything you've been doing on CD Live saved on the hard drive for future CD Live sessions. If you then boot on XP and look on "My Computer" you'll just see the file "pupsave" (I forget actually what the filename is).

It's busted on 7.10 Feisty.

Cheers, Jerry

---

### Post by Howard Kaikow on 2007-05-13
> **the.phantom said:**
> yes you will be able to work firefox ( don't know if t-bird is default mail in fiesty or not?)

changes you make to the firefox and such won't be saved as won't write to the cd ;-D

i used a external modem on the serial port when i was on dialup and was no problem

I find it hard to believe that any OS would not supportan internal Courier modem.

I'm not interested in saving changes from the LiveCD session, but being able to use Firefox would enable me to request help in this forum without shutting down the session and rebooting back and forth to Windows.

---

### Post by Howard Kaikow on 2007-05-13
> **jerrylamos said:**
> On Dapper 6.06 and Edgy 6.10 and a number of other Linux Distros you can have a "persistent" mode where CD Live files, changes, and even package installs are saved on a USB pen drive.  You can even take the CD Live and USB to another computer and continue what you were doing with your files, settings, and installed packages.  

Some distros like Puppy allow you to save your work etc. on a file on XP so you have everything you've been doing on CD Live saved on the hard drive for future CD Live sessions. If you then boot on XP and look on "My Computer" you'll just see the file "pupsave" (I forget actually what the filename is).

It's busted on 7.10 Feisty.

Cheers, Jerry

I'm not really interested in saving anything from the LiveCD session.
I'll likely import the bookmarks from my Windows Firefox, so I can browse.

Mostly, I want to play with vi and/or emacs so I can edit things quickly as needed during the install, or first boot.

I also want to make sure that I can copy the GRUB boot sector to a floppy and the FAT32 drive.

I also want to see what partitions are recognized .

I already have drives partitioned with an ext3 and a swap partition.

When the Select a disk screen comes up during the install, I need to choose "Manually edit partition table", but I do not really need to edit anything, so I'd like to skip the GParted step and go on after that. Not sure how to do that with safety.

---

### Post by Howard Kaikow on 2007-05-13
I just ran LiveCD.
1st time, I got an error "Can't access TTY".
I turned on the printer and plugged in the scanner and tried again. This time it worked.

ALL drives were mounted, so I was able to access all files on the 9 NTFS partitions on the 3 internal drives, the FAT 32 partition on an internal drive, the 3 USB drives, the ZIP drive, and the ext3 partition was available.

1. I opened a terminal window and did a df. The 3 USB drives, Zip drive, FAT 32 partition and the ext3 partition were listed.

2. The FAT32 is listed as a removable drive (/dev/sdf9). Makes no sense (to me).

3. How does  one format a floppy?

4. Tried to set up modem (internal Courier), but did not know which port to pick, so I could not dial out.

5. Interestingly, KPPP is listed as an available download, but Gnome PPP is not.

6. Firefox is installed, but I forgot to check the version.

7. I forgot to set up the printer, so do not know if that will be a problem (Lexmark E312 laser printer).

---

### Post by Howard Kaikow on 2007-05-14
I've tried running from LiveCD, version 7.04.

I installed gnome-ppp, and it successfully identified my modem on ttys1.
I was able to dial out and my ISP confirmed that I was connected.

But, Firefox cannot find any URL.
Evolution can find neither the incoming nor outgoing mail servers.
I cannot ping anyone.
I cannot ftp.

My ISP cannot ping me.

I am using a dialup modem.
Could Linux be trying to go thru the router, not connected to the internet, that I use for my local network?
Is there a linux firewall issue?

Should I try 6.10?

---

### Post by Howard Kaikow on 2007-05-14
Here's more info.

> --> PPP negotiation detected.
--> Starting pppd at Sun May 13 19:30:09 2007
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 12012
--> Using interface ppp0
--> local  IP address [I removed address here]
--> remote IP address [I removed address here]
--> primary   DNS address [I removed address here]

I can ping the local and remote IP addresses, but not the DNS address.

Are the Warnings above relevant to my problem?

---

### Post by aonegodman on 2007-12-11
ditto on "one of the things that impressed me" about LiveCD. I was trying out various pop destro's of Linux, DSL, Pendrive(thinking only on my USB Flash Drive), Ubuntu was the first one to come up recognizing all devices and my broadband and installing all correct drivers. Others, i think it was DSL, killed my USB mouse and graphic and media drivers in Windows and locked up my system. Ubuntu is the first destro of Linux that I have enough confidence in to think maybe I can escape the grasp of an MS based OS finally. What a day that will be. Hallelujah!!!

But in the mean time I'm still looking for some answers here and I know sooner or later I'll catch on and get my system set up right. Thanks! :)

---

