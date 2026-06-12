---
title: "Complete Beginner Here.  Installing on external Hard Drive."
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by The-Master on 2007-01-21
I don't actually have a clue how to install ubuntu on an external hard drive.  I have burned the iso to a DVD.  What should I do now.  Any help would be greatly appreciated.  Thanks:D

---

### Post by xyz on 2007-01-21
First thing is to check your BIOS to see if you have the option to boot from external HD in there.

---

### Post by The-Master on 2007-01-21
Well I think it does because I installed linux on a pen drive before and could boot from that.  Does that mean I will be able to boot from an external one?  Thanks.

---

### Post by xyz on 2007-01-21
Well then I guess it does. I'd make sure just in case.
At boot, press Esc, Delete, F2, F12 or whatever key. It depends on your computer.
Give it a try!
[on external USB drive]("http://www.ubuntuforums.org/showthread.php?t=80811")

---

### Post by JamieC on 2007-01-21
> **xyz said:**
> Well then I guess it does. I'd make sure just in case.
At boot, press Esc, Delete, F2, F12 or whatever key. It depends on your computer.
Give it a try!
[on external USB drive]("http://www.ubuntuforums.org/showthread.php?t=80811")

It does not, there is a big, big difference between booting from USB flash drives and USB hard drives, primarily size.

Some BIOS' support USB-ZIP booting, this however is limited to size, it will boot flash drives, but hard drives will probably be too large to fall under USB-ZIP.

Please confirm you have a USB-HDD boot option (or otherwise the USB hard drive is listed in the boot priority for hard drives).

---

### Post by The-Master on 2007-01-21
> **JamieC said:**
> It does not, there is a big, big difference between booting from USB flash drives and USB hard drives, primarily size.

Some BIOS' support USB-ZIP booting, this however is limited to size, it will boot flash drives, but hard drives will probably be too large to fall under USB-ZIP.

Please confirm you have a USB-HDD boot option (or otherwise the USB hard drive is listed in the boot priority for hard drives).

How do I go about checking this?  Thanks.

---

### Post by Nate7679 on 2007-02-28
Im also having a problem. i set up the installer normally and i used /dev/sda to install GRUB to, but the installer stops at about 15% and gives me the error:

The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.

what should i change?

---

### Post by mosiac on 2007-02-28
> **The-Master said:**
> How do I go about checking this?  Thanks.

There are two ways to check this on my machine

In the bios it lets you select boot order and I noticed I can boot off Mass USB and choose when to, also I can press F12 on my machine to select a boot device.  

It might not be f12 for you but could easily be a key around that area.


Nate:  I had that same problem when I was installing to an external HDD but for some reason I just re did it a couple times and it went through, there should be some proper explination on how to fix that.

---

### Post by Nate7679 on 2007-02-28
I tried that once and i got the same error. But i can try it again if that worked for you.

---

### Post by skiddly on 2007-02-28
[SIZE="5"][/SIZE]I asked similar question in an earlier post advice i was given and am passing on is if you can not boot direct from h/d it will take a long time to load when turning external h/d on as it has to read all files each time, what i did was dual boot pc h/d and use my 320g ext h/d to store everything on from my xp and linux if i can work it out i might partition it but dont think its really essential as i just created a linux folder for linux stuff and xp folder for xp stuff another option im considering for future is installing another h/d to pc

---

### Post by Nate7679 on 2007-02-28
So are you saying that I'm unable to boot from an external hard drive? The computer this is on is used by more people than just me so partitioning my hard drive or booting linux from the computers hard drive at all is out of the question

---

### Post by Nate7679 on 2007-02-28
I found a solution here: [http://ubuntuforums.org/showthread.php?t=308027&page=3](http://ubuntuforums.org/showthread.php?t=308027&page=3)

"i did have this exact problem. All you have to do is before you start installing,
System > Preferences > Removable Drives and Media and deselect the following options
* Mount removable drives when hot-plugged
* Mount Removable Media When Inserted
* Browse Removable Media When Inserted
then when you are on the partitioning step of the installation unmount all disk and proceed...
i think this problem happens because after this step the live cd auto mount the usb disk again. When i did this that problem was solved."

The problem is that I believe i did have those selected when i got the errors. Im not using the  live cd though, im using the installer. would this cause any problems?

---

### Post by Aya Dream on 2007-03-04
> **Nate7679 said:**
> Im also having a problem. i set up the installer normally and i used /dev/sda to install GRUB to, but the installer stops at about 15% and gives me the error:

The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.

what should i change?

Nate I had the same problem and read a thread somewhere that said the following:

This became a problem later when trying to partition the drive and create a file system because the drive was mounted.

To fix the problem, prior to clicking the install icon, go to System > Preferences > Removable Drives and Media and deselect the following options

    * Mount removable drives when hot-plugged
    * Mount Removable Media When Inserted
    * Browse Removable Media When Inserted

I also installed grub to /dev/sda. That all worked for me nicely.

BUT when I re-booted I got to a black screen with a grub> command prompt. Pressing tab gave me a list of commands which I haven't a clue what to do with.

Hope this helps you; can anybody tell me what I should do at this grub> prompt?

---

### Post by Nate7679 on 2007-03-04
Yes, thats what I did and it worked for me, the problem was that it didnt seem to be installed because not even ubuntu booted from a disc could recognize files on the drive.

My friend installed 5.1 on the same external drive, but now im having problems booting from that.

The thread is here: [http://ubuntuforums.org/showthread.php?p=2241937#post2241937](http://ubuntuforums.org/showthread.php?p=2241937#post2241937)

---

### Post by kk0sse54 on 2008-04-11
I have a 144 GB internal hard drive with Windows XP Media Center Edition and a 80 GB external hard drive that i want to install Ubuntu which i have been using for the last 3 months through Vmnplayer but now i want to completely install it as a dual boot. I already checked my BIOs and i am able to boot from an external HD. I kinda got lost in the rest of the thread and i already have the live CD so can anybody explain the installation?

---

