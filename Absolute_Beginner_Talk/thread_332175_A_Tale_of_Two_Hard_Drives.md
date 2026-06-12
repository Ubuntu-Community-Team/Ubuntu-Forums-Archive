---
title: "A Tale of Two Hard Drives"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by scottness on 2007-01-05
Hi folks. I'm a pretty recent switcher to Ubuntu from XP and I have a couple questions about retrieving my backed-up files.

Before installing Edgy to my desktop (after falling in love with how it worked on my wife's laptop), I backed up my files on a Maxtor 80g hard drive.  This still has a full install of XP on it, was my primary hard drive until I upgraded to a 250g Hitachi Deskstar.  Recently, I had some problems with XP that led to a need to completely reformat the 250g drive.  I decided that it was the perfect opportunity to install Ubuntu as I had been threatening to do for months.  So I did.  And I love it, great system...everything runs smoothly.

After backing up my files to the 80g slave drive, I took it out of the case and have it in storage in case I didn't like the linux install and wanted to switch back painlessly.  But now that I know I want to stick with Ubuntu, I have a couple questions.

Will I be able to simply reconnect the slave drive and transfer my files?  If not, what do I need to do to get the two hard drives talking?

And is it possible to dual-boot the machine with this other Windows install?  How would I do that?

Thanks in advance for your help.  I've been able to figure out most of the other startup issues without having to resort to forum support, but google and other searches haven't been extremely helpful to me in this case.

---

### Post by kebes on 2007-01-05
> **scottness said:**
> Hi folks. I'm a pretty recent switcher to Ubuntu from XP and I have a couple questions about retrieving my backed-up files.
First off: Welcome!

> Will I be able to simply reconnect the slave drive and transfer my files?  If not, what do I need to do to get the two hard drives talking?

Short answer: yes it should be easy.

If you install that drive as a slave, it should automatically be detected when you boot into Ubuntu. It will probably automatically mount it, too... but if it doesn't it's quick to open the partition manager and set that drive to mount. Then you can copy files off of it easily.

(btw, what is this other drive formatted as? I'm guessing it was a Windows NTFS drive... in which case you should be able to copy data ~from~ the drive, but be aware that ~writing~ to NTFS drives with Linux is still considered experimental...)


> And is it possible to dual-boot the machine with this other Windows install?  How would I do that?

I believe it's quite possible, yes. However I know that when dual-booting the 'easiest' way is to have Windows installed on the first partition of the first hard drive (windows can be finicky about these things...). As I understand it, you have two drives:

Drive A (older), 80 GB, has Windows and backed up files on it. (NTFS?)
Drive B (new!), 250 GB, has Ubuntu and nothing else. (formatted ext3?)

(if I don't understand your setup then of course the 'how' changes a bit... for instance did you leave empty space on your 250GB drive to install windows?)

In the above case it might be 'easier' to put Drive A as the master and Drive B as the slave. Then you install the Linux bootloader (Grub) to the master boot record (MBR) of Drive A, and it will select whether the Windows gets booted or the Linux gets booted. Configuring this involves editing the "Grub" file which is easy to do. (Make sure you have a LiveCD nearby!)



In any case I think it can be done (certainly worth a try). If you need more details, give us some information on your setup and we'll give more specific suggestions.

---

### Post by louieb on 2007-01-05
During my first Linux install I removed the XP drive just to make sure I did not mess it up. 
Just reconnect it as slave and add this entry to your /boot/grub/menu.lst.
```
title Win XP Home
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1
      boot
```I have a little [more info]("http://louboldt.com/ilinuxgrub.htm") here.

---

### Post by steve.horsley on 2007-01-05
You should just be able to connect the slave drive. But you will need to mount it, which will require use of the command **mount** or editing /etc/fstab. Read here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

Linux cannot write to NTFS partitions though.

---

### Post by scottness on 2007-01-07
Update:

I was able to mount the NTFS drive as slave pretty easily, and after some tinkering was able to get my system to dual-boot using louieb's walkthrough.  Thanks to all of your for your quick and helpful responses.

However, I've discovered another annoying little bug.

How can I get GRUB to recognize my USB keyboard and mouse on system startup?  When I first used louieb's solution, I wasn't sure if it worked because I wasn't actually able to access the GRUB menu to choose which OS to startup.  I eventually was able to work around this by using an adapter to plug my usb keyboard into an analog port, but I'd rather not have to do that with every system restart.  

This is probably also related to another issue I have experienced with my usb keyboard and mouse.  Upon startup, both devices are exhibiting very slow response times...sometimes resulting in locking up on a single key or mouse click.  Nothing permanently damaging, but very annoying.  After checking system messages, I noticed that those usb ports were resetting themselves every few seconds, causing the delay.  A temporary workaround I found was to simply switch usb ports for the keyboard and mouse.  But once again, that's pretty inconvenient to do on every restart.

Any ideas on how to solve these two problems?  Thanks again for your assistance.

---

### Post by kebes on 2007-01-08
For some motherboards there is a BIOS setting like "Enable Legacy USB support". It's worth a try playing with that.

---

