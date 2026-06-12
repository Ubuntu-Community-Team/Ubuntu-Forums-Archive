---
title: "drive formating"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by axemurder785 on 2007-05-21
i have 3 hard drives. one is internal and is almost full. two are external and are 60GB and 320GB. what should i do to use the 60GB one and the internal one for windows, and use the 320GB for Ubuntu Linux Feisty Fawn 7.04? Should i format the drive for windows to ntfs and format the one for linux to ext3?

---

### Post by axemurder785 on 2007-05-21
i really need a reply guys!

---

### Post by axemurder785 on 2007-05-21
can you make it so that a computer uses two drives for windows and one drive for ubuntu linux 7.04?

---

### Post by axemurder785 on 2007-05-21
please o god help me!

---

### Post by axemurder785 on 2007-05-21
Answer Me!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by jerrylamos on 2007-05-21
We don't know much about your hardware or what hardware connection your external drives used, and whether you've used them before or not.  Are they USB?  Are they FireWire?  How much memory do you have?  To some extent that governs which Ubuntu may run.  What's the processor? How fast is it?  Is it 32 bit or 64 bit?  Is it a desktop or laptop?

Anyway in general terms if you have say XP running on the internal hard drive I'd leave it.  Now Dapper 6.06 and Edgy 6.10 have been out a while and are pretty stable.  Feisty 7.04 has some new code to handle different types of SATA drives and such, and sometimes works well and sometimes doesn't.

As an experiment you try running Ubuntu CD Live, log onto the internet, try Open Office, try some usual things and see if it works with your hardware.  If it doesn't, installing may not be much better.  Now CD Live is intended not to mess up your existing system so it may take a few commands to see the hard drive(s).  I don't have any external hard drives to try.

Suppose it ran and you'd like to try an install.  I'd strongly suggest some reference such as "The Official Ubuntu Book" from a bookseller or Amazon.

Assuming Ubuntu rather than Xubuntu or Kubuntu since I don't know your preferences, you select System, Administration, Gparted.

In the upper right corner there's a little arrow box.  You select it to select which hard drive you are interested in.  If it doesn't see your external drives then Ubuntu may not either.  I don't have your setup to try so you'd have to post what you see.

What you want is at least 512 MB Swap, and a 4 GB to 20 GB partition selected for Ext3 and mount point /.  4 GB doesn't leave much room for added applications, 20 GB is fine unless you do a lot of music or photos.

If you give us some more info we might have an idea on how to help you.

---

### Post by axemurder785 on 2007-05-21
i just want to make windows use the two smaller drives and make ubuntu use the big one. i already know the two external hard drives work on ubuntu. i don't care if the internal one does or dosen't because i plan to use it only for windows. How would i format my 320GB drive to Ext3?

---

### Post by drowner on 2007-05-21
> **axemurder785 said:**
> i just want to make windows use the two smaller drives and make ubuntu use the big one. i already know the two external hard drives work on ubuntu. i don't care if the internal one does or dosen't because i plan to use it only for windows. How would i format my 320GB drive to Ext3?

My word.

Two threads and a million bumps.

Did you try searching for this topic?

Formatting the drive is the easy part.

Infact, if you intend to install ubuntu, it will format the drives when you install it, if you like, so there is no need to start partitioning just yet.

My concern is with your grub boot-loader, which tells you which operating system to boot. It will normally write that to the MBR, but if you try and boot your computer without the external drives attached (are they attached by USB) then grub might panic a bit. 

You may need to install GRUB to to the USB drives, but then you need to make sure your BIOS can boot from USB.

---

### Post by axemurder785 on 2007-05-21
i always keep my external hard drives attached. yes they are attached by usb

---

### Post by drowner on 2007-05-21
> **axemurder785 said:**
> i always keep my external hard drives attached. yes they are attached by usb

See

[http://ubuntuforums.org/showthread.php?p=2697389#post2697389](http://ubuntuforums.org/showthread.php?p=2697389#post2697389)

There you say they AREN'T attached to your computer all the time.

And the number of threads and bumps you have done is starting to wear patience thin.

---

