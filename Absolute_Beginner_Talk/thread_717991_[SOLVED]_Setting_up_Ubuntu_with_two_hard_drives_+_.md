---
title: "[SOLVED] Setting up Ubuntu with two hard drives + computer cable problem?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by penguinbreath on 2008-03-07
I have been given a computer which has Kubuntu 7.04 installed on it.  I want to upgrade to 7.10 for GIMP 2.4 support, and I also wish to re-do my current hard drive setup.

I currently have two hard drives in the setup, a 30gb and a 80gb. I wanted the 30gb for backups only in case of a hard drive failure (something like what an external hard drive would be used for), and the 80gb to contain my OS, personal data, and such. I do not want my /home folder on a separate drive from the OS.  My question is, can I do this from a *ubuntu live CD, or will I need a Gparted live CD to do this?

I also have an error when I first start up the computer. It says there is "no 80 conductor cable installed" and that the floppy drive failed.  I have installed a new power supply in this machine, so could this "80 conductor cable" be the power feed to the floppy that somehow was not connected properly?  

Thanks!

---

### Post by wednesday allfather on 2008-03-07
I think that message means you are using a 40 conductor cable, connecting your motherboard to a device.  It should still work, but slowly.  I'd get a new cable.

As for installation, if I understand, you just need any old install disk that will install Ubuntu on your machine.  Once you get it installed, you can use gparted (which you should have installed on your comp after you reinstall your OS) to format the other 30 gig disk to whatever you want.  

There is a lot to be said for /home partition.  I would consider it, unless you have a specific reason not to do it.  I hope that helps you.  Have fun with Ubuntu and your new comp.

---

### Post by Therion on 2008-03-07
Sounds like you want a system drive with a slave; pretty much a simple dual-hard drive configuration like I have.  My suggestion would be to install whatever version of Ubuntu you want on the 80GB drive (I would suggest a clean install, but do as you will) with the 30GB set up as the slave.  Copy to it for backup purposes.  You will partition and format as part of the Ubuntu install, so just format and install to the 80GB drive, leaving the 30GB drive alone, unless you want to "wipe" it.

As for the "error" message you're getting about the floppy drive/80-pin connector... If you don't have a floppy drive installed, I'd go into the BIOS and shut off the option for seeking a floppy at start-up and/or remove the floppy from the boot sequence/chain.  Most likely that would get rid of the error.  Sounds like your BIOS is looking for a bootable floppy at startup.

---

### Post by penguinbreath on 2008-03-07
> Sounds like you want a system drive with a slave; pretty much a simple dual-hard drive configuration like I have. My suggestion would be to install whatever version of Ubuntu you want on the 80GB drive (I would suggest a clean install, but do as you will) with the 30GB set up as the slave. Copy to it for backup purposes. You will partition and format as part of the Ubuntu install, so just format and install to the 80GB drive, leaving the 30GB drive alone, unless you want to "wipe" it.

As for the "error" message you're getting about the floppy drive/80-pin connector... If you don't have a floppy drive installed, I'd go into the BIOS and shut off the option for seeking a floppy at start-up and/or remove the floppy from the boot sequence/chain. Most likely that would get rid of the error. Sounds like your BIOS is looking for a bootable floppy at startup. 

How do I make a drive a "slave"? Is this something I can do in the BIOS or is it something do to with how the cables are connected in the machine?

---

### Post by Therion on 2008-03-07
> **penguinbreath said:**
> How do I make a drive a "slave"? Is this something I can do in the BIOS or is it something do to with how the cables are connected in the machine?
No BIOS adjusting required.

What IS required:  Setting the jumper on the back of the drive.  Move it from Master to Slave position.  There should be a little diagram ON the drive that shows you how to do this, if not... try looking at this pic and follow along (ignore the part about 10-pin drives -- Don't even LOOK at those.  STOP LOOKING!!!):

[img]http://www.networkclue.com/images/peripherals/jumpers.gif[/img]

Set the jumper so the 30GB is a "Slave" (jumper covers pin numbers 3 & 4).  
Connect the drive using the 80-pin connector cable that you're using to connect your current system drive.  There will be a blue connector at one end plugging into the back of the system drive and a (usually) gray one about a foot below the blue one.
Connect the "Slave" to the gray connector.
Mount the drive in the drive-cage, or slot or whatever you have in your case.
Reboot.

---

### Post by penguinbreath on 2008-03-07
> **Therion said:**
> No BIOS adjusting required.

What IS required:  Setting the jumper on the back of the drive.  Move it from Master to Slave position.  There should be a little diagram ON the drive that shows you how to do this, if not... try looking at this pic and follow along (ignore the part about 10-pin drives -- Don't even LOOK at those.  STOP LOOKING!!!):

[img]http://www.networkclue.com/images/peripherals/jumpers.gif[/img]

Set the jumper so the 30GB is a "Slave" (jumper covers pin numbers 3 & 4).  
Connect the drive using the 80-pin connector cable that you're using to connect your current system drive.  There will be a blue connector at one end plugging into the back of the system drive and a (usually) gray one about a foot below the blue one.
Connect the "Slave" to the gray connector.
Mount the drive in the drive-cage, or slot or whatever you have in your case.
Reboot.

Thanks for the help there. Luckily it looks like my 30gb hard drive is already set as slave. 


The computer has two optical drives, a DVD-CD burner drive, and a CD-burner drive. I unplugged the CD burner drive thinking it might have been the cause of the error I was getting. After unplugging it, it seems that it was not the problem, so I narrowed it down to the floppy. I never bothered plugging in the CD-burner drive again. 

Looking at this screen shot (below) of my start-up screen, I am thinking it could be my CD-DVD drive causing the error and the floppy too.  

Apparently copying data from my CD-DVD drive has sometimes been very slow, so could this error have something to do with it? 


Screenshot:

[IMG]http://i211.photobucket.com/albums/bb153/woodland_photographer/IMG_2664.jpg[/IMG]

---

### Post by wednesday allfather on 2008-03-08
It's prolly slow b/c you are using a 40 cable and you need an 80.  Find a cable with a BLUE EDGE.  That is the one you want.  You will see drastic improvement in read speed.

---

### Post by handy on 2008-03-08
> **wednesday allfather said:**
> It's prolly slow b/c you are using a 40 cable and you need an 80.  Find a cable with a BLUE EDGE.  That is the one you want.  You will see drastic improvement in read speed.

I'd be surprised if a cable change makes any noticeable difference to the speed, if you are lucky you will get faster transfers of large contiguous files.

---

### Post by penguinbreath on 2008-03-08
I am very confused here, I need to install a new cable to make the 80 conductor cable  error go away?

[IMG]http://i211.photobucket.com/albums/bb153/woodland_photographer/compute2.jpg[/IMG]

[IMG]http://i211.photobucket.com/albums/bb153/woodland_photographer/computer1.jpg[/IMG]

The drive on the top is the DVD-CD burner, and the one I want working. Its set as a slave, and I probably need to set it as master if its the only CD/DVD drive plugged in?

---

### Post by r5gtt2k3 on 2008-03-08
> **penguinbreath said:**
> The drive on the top is the DVD-CD burner, and the one I want working. Its set as a slave, and I probably need to set it as master if its the only CD/DVD drive plugged in?

Yep, Most hard drives/dvd drives have the jumper diagram on them, Also if you are using the IDE lead, make it so the master (on the IDE lead) points to the dvd drive.

---

### Post by penguinbreath on 2008-03-08
> **r5gtt2k3 said:**
> Yep, Most hard drives/dvd drives have the jumper diagram on them, Also if you are using the IDE lead, make it so the master (on the IDE lead) points to the dvd drive.

Should I replace the cable with a blue edged one?

---

### Post by handy on 2008-03-08
> **penguinbreath said:**
> Should I replace the cable with a blue edged one?

Also, know that the blue or red or whatever colour edge has to go to pin 1, which is always the side where the power cable plugs in, on IDE drives.

You will usually get jumper settings written on top of your hard drive, & at the rear/top or rear, of the DVD/CD drive which explain how to make your particular brand & model of drive a ***M***aster, ***S***lave, ***C***able select.

As I've said before I will be astounded if you notice any speed change in your boot process after changing from a 40 to an 80 cable.

---

### Post by penguinbreath on 2008-03-09
I fixed the floppy drive error by turning off the seek floppy setting in the BIOS. Thanks Therion.

I replaced the old IDE cable for the DVD drive with a newer one I found in my drawer. I set the DVD drive as master with the jumper thing, and plugged the master end of the IDE cable into the DVD drive. I found a diagram that told me which ends went where.
At startup the ?BIOS? still tells me that no 80 conductor cable is installed, however I will just ignore it for now.
    My computer now boots normally without me having to press a button to continue.

I will begin the Ubuntu 7.10 installation shortly after I check over my backups. If all goes well I should be marking this thread solved very soon.

Thanks everyone!

---

### Post by penguinbreath on 2008-03-09
It looks like the installation went well. However I cannot find my secondary hard drive on Ubuntu. Do I have to mount it?

---

### Post by handy on 2008-03-09
> **penguinbreath said:**
> It looks like the installation went well. However I cannot find my secondary hard drive on Ubuntu. Do I have to mount it?

Use the help file that is installed on your computer, you will find it in the menu.

Look for ***fstab***, it will show you how to edit this file to make your slave drive accessible.

---

