---
title: "Format New Drive"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-08-28
I am having some difficulty formatting a new hard drive.  Any suggestions appreciated.  The drive is a Seagate ST3750640NS which I have installed in an external USB mounting and what I wish to do is to format the drive to ext3.

Originally I booted to a live CD and opened Gparted and the drive was found.  I selected the volume and set up the job to format to ext3.   The problem is that the format process failed.  The format label (ext3) had been set but the drive did not format.  There was no other information presented.

When I now either refresh Gparted or even boot fresh, the drive is not found.  If I boot normally and run sudo fdisk -l the drive is not there.

Could anyone please tell me the proper steps to follow to get this recognized and formatted?

---

### Post by apjone on 2007-08-28
take a look at [http://www.hackjob.org/howto-formatting-and-partitioning-your-external-usb-hard-drive](http://www.hackjob.org/howto-formatting-and-partitioning-your-external-usb-hard-drive) 

or 

[http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=BPf&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=ubuntu+external+usb+hard+drive+format&spell=1](http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=BPf&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=ubuntu+external+usb+hard+drive+format&spell=1)

---

### Post by dwhitney67 on 2007-08-28
When you plug your drive in, do you know what device it sits on?  If is USB, then it is probably /dev/sdb1 or possibly /dev/sdb2.

If it is not already mounted, then I think you can verify which one it is buy issuing a command like this:

[FONT="Courier New"]$ sudo cat /dev/sdb1  (or sdb2)[/FONT]

If you see any output (other than an error) then that's the device assigned to your drive.

To make an ext3 filesystem on that device, run this command:

[FONT="Courier New"]$ sudo mke2fs -jv /dev/<xxx>[/FONT]

replacing the <xxx> with the appropriate sdb device.

Then, if needed, try to mount the drive by issuing a command such as the following:

[FONT="Courier New"]$ sudo mount -v -t ext3 /dev/<xxx> /some/mount/point[/FONT]


P.S.  I am definitely not an expert in these matters.  Normally if a drive is formatted correctly, HAL should be able to handle it and automagically mount it for you.  If the drive has an assigned volume label then you can be assured that HAL will always mount the drive at the same place, regardless of the /dev device handling the drive.  Alternatively you can place an entry within the /etc/fstab file, however this is less elegant in cases where the /dev/ device handling the drive can change.

---

### Post by Marat Galiev on 2007-08-28
do this with partition magic program:)but it's windows way:)
use man mkfs.ext3.

---

### Post by expatCM on 2007-08-28
Thank you all for your comments and suggestions.  The status has changed quite a bit now, I think for the better but I am not so sure that I trust this drive.

If I have the drive connected and powered on when I power up the PC, the PC will stall in loading the CMOS.  No idea why,  but hang it does.  The message says "Auto detecting USB mass storage devices..   Device #01" and then it stops.   I can only start the PC if I power off the drive and power on the PC again.

Not making any progress in Ubuntu I booted to Windows.  Not been there for months and months. I had huge problems in getting the drive to be identified by the system.   Nothing would see it.  Eventually Partition Magic would find and read the drive.  It had been terminating with an Init Failed  Error 100 notice which means the partition table is bad but it does not say which partition table (there are three other drives on the system).

Eventually I have managed to format the drive to ext3 using Partition Magic.  The drive is now recognized in Ubuntu.   But it still hangs the PC if it is powered on when I power up the PC.

Does anyone happen to know of any software I can use to effectively stress test the drive?  I want to be as certain as possible that the drive is not going to fail in light of the difficulty in getting it recognized and formatted....

---

### Post by dwhitney67 on 2007-08-28
It's possible that you do not have a bootable image of any sort on the external drive and that your bootloader is attempting to boot from USB, before CD-ROM, and HDD.

Try booting into Ubuntu first, and after that is complete, then power-on your external drive.

---

### Post by Marat Galiev on 2007-08-28
hmm, you choose windows way?:)
but it help you:)

---

### Post by expatCM on 2007-08-28
Well it was not really a choice to use the Windows approach ... there was no alternative since I could not get the drive to be identified in Ubuntu.   Lucky that I kept a Windows partition.

dwhitney67 - nice thought but this behavior is shown before the boot loader kicks in.  So I guess it is a BIOS related issue but I do not understand why.   I have a number of 500GB drives which are used as external drives through USB.  The only difference is that the drive in question is a 750GB drive.  If a 500GB drive can be powered on and still allow the system to boot, I cannot quite see what is the big deal with a 750GB drive.  So perhaps it is a problem with the drive?

This is why I would like to find some software which makes the drive do a lot of work.....   testing it and pushing it seems important before I can trust it with real data...

---

### Post by dwhitney67 on 2007-08-28
Well, sorry I couldn't help.  A couple of other forum members have been trying to get their "MyBook" drives working today so I thought I could help.

I sure wish I could be where your at to enjoy a cold Chang beer.

---

### Post by expatCM on 2007-08-28
funny, I was practicing with Chang yesterday and right now using coffee to make the day look better :)

---

### Post by expatCM on 2007-08-29
I think one approach to testing the drive will be to find a program that makes three passes to write over the drive.  The first pass writes 1, the second pass writes 0 and the final pass writes a random character.  My thinking being that if it can fully write to the whole of the drive then the drive is probably sound.

Anyone happen to know the name of the program?

---

