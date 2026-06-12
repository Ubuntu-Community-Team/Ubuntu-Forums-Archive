---
title: "How do I get Ubuntu v. 6 to actually run?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by JEBB on 2006-07-04
I had v. 5.10 on my Compaq 1688 but it wouldn't allow me to save files to a floppy.  I found out here that there is a problem with that part of 5.10 so I downloaded version 6.06 from the iu site.  After loading it twice I kept getting the same problem of it not being able to boot.  It would stop the boot process and restart the computer.   I found that others had had the same problem.  The alternate version was suggested, so I downloaded that.  So I've loaded it and installed it.  Booting it gets further than the first attempts but after putting in my id and password it leaves me with a command line prompt that begins with my id:  jim@ubuntu: ~$ 

Now what???

This is a great frustration.

---

### Post by meng on 2006-07-04
Are there any messages about X failing? Are you sure you downloaded and installed the desktop version not the server version?

---

### Post by xael on 2006-07-04
Jim,

What happens when you try to start x with the command **startx**?, do you receive any messages?.

---

### Post by JEBB on 2006-07-04
My understanding is that the desktop version is for running Linux from the CD.  

I downloaded the server install version but it wouldn't complete the boot process once installed on my Compaq.

My latest download was 'PC (Intel x86) alternate install CD' that got me into this latest situation, the command line problem noted in the intial post.  

A further frustration is that I have not been sent a password to sign up for a free disk.  

Is it possible that different download sites and the mailed versions of Ubuntu 6 have differences?

---

### Post by JEBB on 2006-07-04
I entered the command startx.  The reply line as the same as a bunch of others I tried:

-bash: startx: command not found

---

### Post by meng on 2006-07-04
If you downloaded and installed the server version, then X is probably not installed. (You've installed Ubuntu without a GUI.) That's why your login is command-line only. You'd be wanting to download and install the desktop alternate version.

---

### Post by catlett on 2006-07-04
You only have the server addition installed. No problem though. Just issue this one command and you will have gnome 
```
sudo apt-get install ubuntu-desktop
``` After it installs reboot and you will be in.
You may have to load your apt cache first. If it doesn't find the package update then run the ubuntu caommand ```
sudo apt-get update
``` You will need to be connected to the internet while doing this.

---

### Post by JEBB on 2006-07-04
I reinstalled the alternate version and used the first selection, text, not server.  It has now loaded.  Thanks for your help.

---

