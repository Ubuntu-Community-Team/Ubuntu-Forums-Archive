---
title: "Something wrong with my external drive."
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-07-23
Okay - I'm using my friends external drive, he formatted it on a PC so its FAT32.

When I first got it, I had to mount the drive manually threw the fstab. I did this and successfully moved my data on to it, and even moved a few movies to a PC and a iBook. One day, the drive just appeared as PB_SAFE as an external USB device *(usually i would just open media/fileserver all the files would be there)* and now whenever I try to plug it into the iBook or a PC I get *"This device needs formatted before it can be read"*. 

I have not made any changes to the file structure *(FAT32,ext3,NTFS,etc)* and I'm sure of this as all my mates original backup files are still on it.

Help?

---

### Post by ayenack on 2007-07-23
Try using Test Disk. You can download it from the repo's. Use Synaptic or just do it from the command line. It's a great little app for recovering partitions and data.

sudo apt-get install testdisk

Once installed just type testdisk in terminal and it will open and ask you to enlarge the window after doing this just follow the instructions, it's very simple to use.

Best of luck. ayenack.

Let me know how it goes.

---

### Post by auraithx on 2007-07-23
I think you've misunderstood. The drive still works fine for me on Ubuntu. However, Mac/PC users are unable to see it without formatting the disk.

---

### Post by ayenack on 2007-07-23
[Test Disk]("http://www.cgsecurity.org/wiki/TestDisk") works on Mac Win XP/NT/95/98 and others. Go to [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk") web site and download for each OS plug in the drive and your away. You can recover the drive not to sure what this will do to the functionality under the other OS's but it should be fine I think.

Well good luck. Post back if any probs.

---

### Post by auraithx on 2007-07-25
The program was pretty useless tbh. The drive works fine and that's what it told me.

However, The drive is now showing as read-only in Ubuntu. :mad:

---

### Post by auraithx on 2007-07-25
Okay - now the drive doesn't work at all.

I can't even see it when I go to my sudo fdisk -l

---

### Post by auraithx on 2007-07-26
bump - I can see it again (turned out to be a dodgy wire)

but it's still all READ-ONLY


HELP

---

### Post by ayenack on 2007-07-27
Not bumped as you put it, I had a few problems of my own.

You may have some issues with permissions if it's read only. Log in as root right click on the drive and select permissions and change to your user name. To log in as root you will have to go to System>Administration>Login Window click on Security Tab the Allow local system administrator login. After you've done this click on System>Administration>Users and Groups then double left  click root and input a password of your choice. You may also want to change the root User Privileges which is in the same options box.

Best of luck. ayenack.

---

### Post by auraithx on 2007-07-27
even when logged in as root it gave me an error that it was a read-only disk..


:confused::confused:

---

### Post by Blutack on 2007-07-27
You checked the system log with the disk under load?  It could be heading out and intermittantly having problems.

---

### Post by auraithx on 2007-07-27
> **Blutack said:**
> You checked the system log with the disk under load?  It could be heading out and intermittantly having problems.

:confused:

---

### Post by Blutack on 2007-07-27
Unmount and unplug the drive
System --> Admin --> System Log Viewer
Watch the /var/log/messages as you plug the drive in again and paste the relevant bits of output.

---

### Post by auraithx on 2007-07-27
Jul 28 00:46:38 glasgowm-desktop kernel: [127808.477620] usb 4-8: new high speed USB device using ehci_hcd and address 11
Jul 28 00:46:39 glasgowm-desktop kernel: [127808.611688] usb 4-8: configuration #1 chosen from 1 choice
Jul 28 00:46:39 glasgowm-desktop kernel: [127808.611937] scsi10 : SCSI emulation for USB Mass Storage devices
Jul 28 00:46:44 glasgowm-desktop kernel: [127813.607643] scsi 10:0:0:0: Direct-Access     ST325082 3A               0000 PQ: 0 ANSI: 0
Jul 28 00:46:44 glasgowm-desktop kernel: [127813.609786] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Jul 28 00:46:44 glasgowm-desktop kernel: [127813.610732] sdc: Write Protect is off
Jul 28 00:46:44 glasgowm-desktop kernel: [127813.611964] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Jul 28 00:46:44 glasgowm-desktop kernel: [127813.612851] sdc: Write Protect is off
Jul 28 00:46:44 glasgowm-desktop kernel: [127813.612867]  sdc: sdc1
Jul 28 00:46:44 glasgowm-desktop kernel: [127813.628583] sd 10:0:0:0: Attached scsi disk sdc
Jul 28 00:46:44 glasgowm-desktop kernel: [127813.628656] sd 10:0:0:0: Attached scsi generic sg4 type 0

[b]Edit : now the the drive is letting me edit files - what the hell is wrong with this thing it's spazing out.
[/b]

**edit2 : all the files are locked again**

**edit3: the drive appears to be unlocked again :/ (after turning it off and back on again)**

---

