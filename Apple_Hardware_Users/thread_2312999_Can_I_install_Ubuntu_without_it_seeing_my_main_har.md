---
title: "Can I install Ubuntu without it seeing my main hard drive?"
date: 2016-02-08
forum: Apple Hardware Users
---

### Post by noah33 on 2016-02-08
Here's what I want to do:
I want to dual boot Windows and Ubuntu. I have a Live USB ready to go, but I don't want to risk installing Ubuntu on my main hard drive, which has my main OS on it. Is there a way I can stop the Ubuntu installer from seeing my main hard drive and only see my external hard drive I plug in? Thank you!

Cheers!

EDIT: I should have probably mentioned this before. I'm using a laptop!

---

### Post by QIII on 2016-02-09
You can simply unplug your internal drive and start your machine with your live media attached.  Then install to the external drive.  That's the most certain way to make sure you don't make a tragic error.

---

### Post by noah33 on 2016-02-09
I'm using a laptop. I'd rather not take apart my laptop 
Is there another possible way? Can I use a partition editor to temporarily "unsee" it? Possibly temporarily disable it?

---

### Post by C.S.Cameron on 2016-02-09
Unplugging a laptop hard drive is not too hard and is worthwhile, otherwise when you get to partitioning when installing use "Something Else" and be careful.
Make sure you are installing the O/S to the correct drive and confirm "Device for boot loader installation" points to the USB drive, (ie sdb not sdb1).
I have tried but not had much success hiding the internal drive from the installer.

---

### Post by sudodus on 2016-02-09
A couple of things are easy to remove and install in laptops: The hard disk drive and the RAM. Like *QIII* and *C.S.Cameron* I recommend that you remove the hard disk drive. That is the only way to be 100% sure that you avoid install anything into it.

---

### Post by noah33 on 2016-02-09
I have a laptop, though. The screws are not common and require a certain screwdriver. I don't want to take it apart. Is there any other method?

---

### Post by sudodus on 2016-02-09
If your computer is running in UEFI mode: ***No***

If your computer is running in the old BIOS mode: Yes, according to the instruction by C.S.Cameron in post #4.

---

### Post by QIII on 2016-02-09
You may be able to disable the internal drive in your BIOS/UEFI.

---

### Post by yancek on 2016-02-09
You need some familiarity with Linux naming conventions for hard drives and partitions and knowledge of a few commands to identify hardware along with the size of drives.  Run:  sudo fdisk -l after you boot the Ubuntu medium and you will see output on the drives attached with the partitions as well as the size.  This should help you identify which is the internal drive so you don't overwrite it.  A brief outline of drive/partition naming at the link below, many other explanations from an online search although I would agree removing the drive is probably the most fool-proof method.

 [http://askubuntu.com/questions/56929/what-is-the-linux-drive-naming-scheme](http://askubuntu.com/questions/56929/what-is-the-linux-drive-naming-scheme)

---

### Post by sudodus on 2016-02-09
@noah33

We don't know what computer you have and how you are using it now. This can explain our different replies: We are guessing and trying to think of possible cases, problems and possibilities.

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- BIOS mode or UEFI mode

- and how you intend to use the computer.

It helps us to give you good advice.

---

### Post by grahammechanical on 2016-02-09
Guessing is correct.

For example, the Disks utility has an option to put a drive into standby mode. I am guessing that we can use Disks to do that from a live session. But when we then run the installer and the partitioner scans the drives for partitions will the drive be taken out of standby mode? I am not about to experiment with my own machine when the most effective answer has already been given.

---

### Post by kurt18947 on 2016-02-09
> I would agree removing the drive is probably the most fool-proof method.

It is. For instance, older Thinkpads are super easy. They require only one screw removed from a little cover and slide the hard drive out.  The screw is a common phillips head. Other machines might require removing the keyboard - HP Mini netbook was like that. If it were possible to 'make the internal hard drive invisible' via BIOS/UEFI settings, that might be the most practical when installing Ubuntu on the external drive. The machines I've messed with - only 1 UEFI so far - I can set up so if there's an external hard drive present, it will look there for a bootable device. If none is found it will boot from the internal hard drive. Yes using the 'something else' in the installer requires care and a little understanding.

---

### Post by noah33 on 2016-02-09
Macbook Air 2014 Running Windows
1.4 GHz Intel Core i5
4 GB 1600 MHz DDR3
Intel HD Graphics 5000 1536 MB
BIOS
I want to dual boot Ubuntu on my external hard drive. I don't want the installer to see my main hard drive. I *won't* take apart my laptop
I know how to boot into the BIOS and everything. I know how to use unetbootin. I've installed Linux onto my EXHD before, but not in the way I like it. I want to be able to use a Live USB (Which I already have set up)

---

### Post by howefield on 2016-02-09
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by sudodus on 2016-02-10
When you are sure that your computer is running BIOS mode, you can install to the external drive according to the instruction by C.S.Cameron in post #4 :-)

Edit: This is how to install 'an installed system' into an external drive. (Your last sentence in post #13 make me unsure what you want. A persistent live drive is another alternative.)

---

