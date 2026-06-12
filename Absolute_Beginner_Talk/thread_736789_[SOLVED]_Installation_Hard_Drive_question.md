---
title: "[SOLVED] Installation_Hard Drive question"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by kgriff on 2008-03-27
I'm brand new to Ubuntu, and mostly new to Linux.  Ran Red Hat several years ago, but for many reasons, had to revert to Windows.  Now I'm happy to be back, and plan to stay.  I'll try to keep it brief, but here's my story so far:
Computer
Asrock K8NF6G-VSTA Motherboard
512MB RAM
Onboard video (Nvidia GeForce 6100)
Onboard audio
Onboard lan
2 SATA drives
1 IDE drive
1 DVD/CD writer

I unplugged the SATA drive that Windows is installed on prior to installation of Ubuntu.  The DVD and IDE are on the same bus, with the IDE as master.  Ubuntu booted live and ran fine.  Installation was a breeze.  After installation, however, on the first reboot, just after the bios POST I got the message "Error Loading Operating System"  A bit of troubleshooting later and I reversed the IDE devices so that the DVD is master and the IDE HDD is slave.  This allowed Ubuntu to boot and all is well.  Currently I'm in the process of getting back up to speed with Linux.
There is one hitch, however.
I can mount the DVD/CD drive, but cannot mount the IDE drive, hda.  At times, I can see hda in the Places menu, but it will not mount, at other times it does not even show up in the menu.  For instance, yesterday I could see hda in Places, but attempts to mount resulted in an error something like "Unable to mount hda".  (I didn't write down the error message.)  Today, after I started the machine, I don't even see hda in Places, though it does show up in Device Manager.  Any suggestions, short of reverting to hda as master and CD as slave?  I believe that, if I do that, Ubuntu will not boot.
Thanks for reading this far through my long-winded dissertation and thanks in advance for any assistance.

---

### Post by Moop on 2008-03-27
You didn't need to disconnect the windows hdd before installing Ubuntu. I'm not sure if you're trying to mount a windows or linux partition but you can find a good guide for doing both here. [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Samurai Penguin on 2008-03-27
I'm running Ubuntu 7.10 32-bit and when I go to PLACES > COMPUTER
I see the hard drive but it's not labeled hda, it's labeled FILESYSTEM
Also, when I right-click on the Drive, it has no mount/unmount option.
What version of Ubuntu are you using?

---

### Post by kgriff on 2008-03-27
First, I have a question.  I'd like to thank Moop, but don't know how.  What is the method for posting a thanks?

I know I don't have to unplug the Win drive before installing Ubuntu but, believe it or not, there was a reason, albeit a silly one.  I've seen people accidentally overwrite the wrong drive when installing an OS by not paying attention to what they were doing.  To save myself from my own stupidity and make sure it doesn't happen to me, I unplug the drives I don't want to mess with.

Although your link didn't give me the answer, it got me to the right place.  
sudo fdisk -l gave the following information for the drive in question:  /dev/hdb doesn't contain a valid partition table.  A little nosing around and I found that I had set the master/slave jumper wrong.  Set the jumper correctly and, viola, everything works as it should.

And, nevermind about the thanks question above.  I finally saw the Thanks icon at the bottom of posts.

---

