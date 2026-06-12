---
title: "Failed to install boot loader on PowerBook G4"
date: 2006-06-14
forum: Apple PPC Users
---

### Post by cgreene1122 on 2006-06-14
I really need help. 
I'm new to Linux and wanted to install Ubuntu on my last revision PowerBook G4 (Double-Layer SD) and first I tried to install Breezy, but CD was not recognized because the computer was so new. Well, now Dapper Drake is out and I was so exited when the CD boot. But, during the install process, an alert came up and told me that it failed to install the boot loader. Sorry that I don't have the exact message written down, I will soon.
Does anyone know what I should do now?

Thanks in advance!

---

### Post by tidris on 2006-06-14
How is your hard disk partitioned?
Which CD did you use to install ubuntu?
What was the specific error message you got?

---

### Post by cgreene1122 on 2006-06-14
Okay, here's all the details.

I have an 80GB Hard Drive,which ends up to be around 74.8 GB or so. First thing I did was repartition my Disk so I would have 60 gigs for mac os x and about 15gb for ubuntu. They were both formatted in mac os x extended (journaled). I then started up from the Ubuntu Dapper Drake Desktop CD (DVD in my case, since the iso was over 700 MB) and when I got to the partition section of the installer I deleted the 15GB partition and then went back and told the installer to install in the largest continuous free space on my main drive.
It went through all the steps in the installer until it got to the point of installing yaboot. Right in the middle of the installation of yaboot, an error message came up, saying, "Error- Failed to install boot loader"
Then, when I pressed OK, a big window came up, and this is what it said:

Installer Crashed

We're sorry, the installer crashed. Please file a bug report at [https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug) and a developer will attend to theproblem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attatch the files /var/log/installer/syslog, /var/log/syslog, and /var/log:

Traceback (most recent cll last):
File "usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
File "usr/bin/ubiquity", line 55 in install
    ret = wizard.run()
File "usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 264, in run
    self.progress_loop()
File "usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui", line 538, in progress_loop
   raise RuntimeError, ("Install failed with exit code %s; see"

RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog



That's what it spit out to me. I would appreciate any assistance, since I'm running OSX, my only OS, off of a firewire drive until I can get Ubuntu installed.

---

### Post by cgreene1122 on 2006-06-14
I'm going to download the DVD iso and try it that way. It could be that the installer is having trouble because I burned a CD iso onto a DVD.

---

### Post by tidris on 2006-06-14
You could try installing yaboot by hand while booted from the Desktop DVD. I had to do that for my dual G5 due to an issue related to serial ATA hard disks. I describe how I did that in this thread:

[http://www.ubuntuforums.org/showthread.php?t=189133&page=3](http://www.ubuntuforums.org/showthread.php?t=189133&page=3)

Another thing to try is burning the iso image to a CD and installing again. I say that because I had a bad experience trying to install some LINUX distribution from a DVD last year. It didn't work right until I burned it to a CD. My Ubuntu 6.06 Desktop iso is 701 MB but I had no problem burning it on a CD with DiskUtility.

---

### Post by cgreene1122 on 2006-06-14
Thanks, Tidris, for that suggestion! I would not have thought about installing yaboot by hand because I am most definately a beginner in terminal. But I'm going to give it a shot. I'll tell you how it ends up.

---

### Post by tomos on 2006-06-15
If it's anything to you, I can tell you that I have successfully installed to a machine just like yours.  I just cut the hard drive into 2 parts, one for mac osx and another free space for Dapper.


-tomos

---

