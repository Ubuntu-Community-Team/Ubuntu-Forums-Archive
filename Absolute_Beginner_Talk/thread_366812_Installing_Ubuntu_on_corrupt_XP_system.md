---
title: "Installing Ubuntu on corrupt XP system"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by vckeating on 2007-02-21
Hey all.

I've got a corrupt XP system here that I need to retrieve data from.  I thought, 'hey, I'll just install Ubuntu, retrieve the files from the Windows partition, and I'm good to go.'  

The problem is when it comes to partitioning the free space drive - I can't defrag the drive (since XP is dead) and I'm getting the big "you're going to destroy data on the partition" message.  If the thing is not defragged, is there a chance it will blow away existing files by partitioning the free space?  

Any suggestions would be very helpful!!  

- Vincent

---

### Post by teaker1s on 2007-02-21
use a live distro and mount the hard drive and remove your files or plug into another xp machine as slave drive and copy files off

---

### Post by vckeating on 2007-02-21
Hey, thanks for the quick reply - I've already tried this one, but the laptop that I'm working on doesn't have enough RAM to operate the live CD effectively.  For instance, it took almost 10 mins to bring up a command prompt window, and that's without the actual 'prompt' (which never came).

- Vincent

---

### Post by teaker1s on 2007-02-21
how big is the laptop hard drive in gb

---

### Post by vckeating on 2007-02-21
It's a 20GB drive, showing 8.2GB currently free.

---

### Post by george29 on 2007-02-21
there are other liveCD which you could try such as damn small linux [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

which is a debian derived distro - designed to be light weight, but fully functional.. 
    * Boot from a business card CD as a live linux distribution (LiveCD)
    * Boot from a USB pen drive
    * Boot from within a host operating system (that's right, it can run *inside* Windows)
    * Run very nicely from an IDE Compact Flash drive via a method we call "frugal install"
    * Transform into a Debian OS with a traditional hard drive install
    * Run light enough to power a 486DX with 16MB of Ram
    * Run fully in RAM with as little as 128MB (you will be amazed at how fast your computer can be!)
    * Modularly grow -- DSL is highly extendable without the need to customize

this should allow you to mount your laptop partitions and then copy them off onto an external hard drive or usb flash key.  

george

---

### Post by tgalati4 on 2007-02-21
Try damn small linux (damnsmalllinux.org), it's only 50MB, runs well in 32 or 64MB.  It will allow you to mount the drive, attached a USB memory stick copy files, set up a quickie ftp server from which you can down load files to another machine through ethernet.

The alternative is to use the Ubuntu Live CD and go into the options and load a rescue shell.  Only a text console, so you need to know what you are doing.

You are on the right path.  Don't mess with the existing drive, only mount it to read off of it.  Only after your files are recovered should you think about defrag and repartitioning.

---

### Post by tgalati4 on 2007-02-21
Well, that's two votes for DSL for older hardware.

---

### Post by george29 on 2007-02-21
there is also puppy linux 

[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

which according to the website 

    * Puppy will easily install to USB, Zip or hard drive media.
    * Booting from CD, Puppy will load totally into RAM so that the CD drive is then free for other purposes.
    * Booting from CD, Puppy can save everything back to the CD, no need for a hard drive.
    * Booting from USB, Puppy will greatly minimise writes, to extend the life of Flash devices indefinitely.
    * Puppy will be extremely friendly for Linux newbies.
    * Puppy will boot up and run extraordinarily fast.
    * Puppy will have all the applications needed for daily use.
    * Puppy will just work, no hassles.
    * Puppy will breathe new life into old PCs

---

### Post by vckeating on 2007-02-21
Hey - thanks guys.  I'll try the DSL and see where it leads me.

- Vincent

---

### Post by ibanez on 2007-02-21
I also vote puppy linux.
You'll find it is a far more usable desktop than DSL. I've used both and think puppy will have everything you need.

---

### Post by vckeating on 2007-02-23
Hey all.

Just wanted to let you know that DSL did exactly what I needed it to - I recovered the files from the xp box and then installed Ubuntu.  :)

Thanks for all your help!

- V

---

### Post by linux_kid on 2007-02-23
That's a score for DSL :popcorn:

---

### Post by tgalati4 on 2007-02-23
DSL Rocks!
Good for you and welcome back to the Ubuntu fold.  Now get back into the fight.  The enemy is all around us.

---

