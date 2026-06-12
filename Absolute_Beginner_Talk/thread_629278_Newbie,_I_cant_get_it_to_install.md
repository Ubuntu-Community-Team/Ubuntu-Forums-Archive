---
title: "Newbie, I cant get it to install"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by 1967tempest on 2007-12-02
Hello:  
     I am new to Ubuntu.  I stumbled across it when I was looking for a webpage.  I downloaded the LiveCD and have used this platform.  I like it alot.  So I tried to install it but when I did I got "Error 17".  So I downloaded the alternate CD and did the text based install with the same result.  I am installing it throught the guided partioner, on an IDE hard drive.  I tried to install it on one of the SCSI drives I have with the same result.  I am using a wireless network connection that Ubuntu does not find during install.  ANd the wired ethernet adapter does not have a cable to it when I installed.  Do you guys have any answers??  I looked through the forum and didn't see anyone with the same error.  I cant wait to get this thing up and running.  It looks like a Kick butt alternative to Windows.  I am running XP Pro SP2 on the same machine.

Thanks

---

### Post by njparton on 2007-12-02
That's an issue with grub (the bootloader).

The best thing to do is unplug all your other hard drives whilst you install to make sure that grub is put in the correct location (just accept the default).

If you're trying to dual boot with windows on the same hard drive post back here first as that's a different situation!

---

### Post by alienexplorers on 2007-12-02
Why not just use the super grub disk and setup for dual boot.

---

### Post by Gone fishing on 2007-12-02
That a problem with Grub it thinks the root partition is not where it is and your grub menu will need changing. 

I'm wondering if you have several hard drives?

I have to say I always put grub on linux partition (rather than the MBR) and use a boot loader called GAG it allows me to easily add other OS (I like BeOS) and is dead easy to configure and doesn't frighten the wife.

---

### Post by 1967tempest on 2007-12-02
Yes I have more than one hard drive.  I have 5 installed.  4 SCSI running off of the internal scsi card  Adaptec 7902.  and one IDE 120GB.  I tried to load it on the 120.  After the install was done  I get the menu to choose XP or Ubuntu.  When I choose ubuntu, it starts to load but then I get the error.  Can I load Ubuntu onto the same HDD as XP???  I thopught the partioner would erase it??  I will try to do what the previous poster said, buy removing all of the other HDD's and try to just let it ride.

Thanks again.  I cant wait to see how fast it really is on a 2 CPU tower!!!!!!

Dave

---

### Post by Gone fishing on 2007-12-02
Yes you can install onto the same HD as XP obviously it will need it's own partion The installer can resize the ntfs partition although you shoud backup your data I've neverhad a problem with data loss. 

Obviously the during the install grub is getting confused about your hard drive order have a look at this 

[http://www.justlinux.com/forum/showthread.php?threadid=149484](http://www.justlinux.com/forum/showthread.php?threadid=149484)

---

