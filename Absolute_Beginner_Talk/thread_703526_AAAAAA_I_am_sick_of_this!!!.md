---
title: "AAAAAA I am sick of this!!!"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2008-02-21
For 4-th time in 5 months Ubuntu screws me up. What happens is that I turn on my computer and I get a message:
Grub failed to load
error 17

I haven't done anything on the last 3 linux boots except check my email (yahoo) and that's it. I don't know why it does it. I have never messed with the grub (well I am scared of it after the first 3 times it did this). Why is it happening - I mean everything is working fine and then it just crashes? Only thing I have done before that happened actually is to plug in a USB - something i never had done in linux but it would be rediculus if this is the source of the problem.

---

### Post by dca on 2008-02-21
The same thing happens in Windows if it's not recognized or is too new that it requires special drivers or has special encryption software.  Only in Windows it's called BSOD (Blue Screen of Death) and references kernel_drivers or something there-abouts...
 
I used to have a problem w/ this thumbdrive that had this built-in security measure for asking for a username and password in order to access the data on it...

---

### Post by karlo on 2008-02-21
> **KOTAPAKA said:**
> For 4-th time in 5 months Ubuntu screws me up. What happens is that I turn on my computer and I get a message:
Grub failed to load
error 17

I haven't done anything on the last 3 linux boots except check my email (yahoo) and that's it. I don't know why it does it. I have never messed with the grub (well I am scared of it after the first 3 times it did this). Why is it happening - I mean everything is working fine and then it just crashes? Only thing I have done before that happened actually is to plug in a USB - something i never had done in linux but it would be rediculus if this is the source of the problem.

When booting up (before Ubuntu starts), is your usb plugged in?

---

### Post by EXCiD3 on 2008-02-21
> **KOTAPAKA said:**
> For 4-th time in 5 months Ubuntu screws me up. What happens is that I turn on my computer and I get a message:
Grub failed to load
error 17

I haven't done anything on the last 3 linux boots except check my email (yahoo) and that's it. I don't know why it does it. I have never messed with the grub (well I am scared of it after the first 3 times it did this). Why is it happening - I mean everything is working fine and then it just crashes? Only thing I have done before that happened actually is to plug in a USB - something i never had done in linux but it would be rediculus if this is the source of the problem.

One thing I noticed with my specific external hard drive was that if it was plugged in and turned on I would get Error 17. Also I have noticed that my new external drive does NOT do this, and my ipod being plugged in will prevent my laptop from booting past the bios. Check and make sure none of your hardware being attached could be causing this just in case that is the problem.

---

### Post by KOTAPAKA on 2008-02-21
how do I get around it I mean I am sick of it - I had a lot of stuff on my linux and all is lost as the only option I see is to reformat the partition it is on. I've had various errors but the ones I remember are 17(now) and 22 the previous one. So please explain in simple terms what is the cause of the problem so that I won't make the mistake again.

---

### Post by run1206 on 2008-02-21
i've received this message a few years ago, i had to re-install both my Windows and Linux partitions (dual-booting). Your GRUB might be missing the files needed to load

---

### Post by EXCiD3 on 2008-02-21
> **KOTAPAKA said:**
> how do I get around it I mean I am sick of it - I had a lot of stuff on my linux and all is lost as the only option I see is to reformat the partition it is on. I've had various errors but the ones I remember are 17(now) and 22 the previous one. So please explain in simple terms what is the cause of the problem so that I won't make the mistake again.

What I have done is just make sure the devices are not plugged in until after you have selected your OS in grub. Everything should continue fine from that point on. I don't know if there is anything you can do to fix this problem. I have a feeling it has to do with the ability to boot from these drives and it is conflicting with the drive names/locations.

here are the meanings of errors 17 and 22 but i'm not sure how to explain them as i dont quite completely understand them myself:

> **17** : **"Invalid device requested"** This error is returned if a device string is recognizable but does not fall under the other device errors.> **22** : **"Must load Multiboot kernel before modules"**
 This error is returned if the module load command is used before loading a Multiboot kernel.  It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of location of such modules to a non-Multiboot-aware kernel.

---

### Post by oilchangeguy on 2008-02-21
> **KOTAPAKA said:**
> For 4-th time in 5 months Ubuntu screws me up. What happens is that I turn on my computer and I get a message:
Grub failed to load
error 17

I haven't done anything on the last 3 linux boots except check my email (yahoo) and that's it. I don't know why it does it. I have never messed with the grub (well I am scared of it after the first 3 times it did this). Why is it happening - I mean everything is working fine and then it just crashes? Only thing I have done before that happened actually is to plug in a USB - something i never had done in linux but it would be rediculus if this is the source of the problem.

you have another thread saying that you're trying to install ubuntu from a usb drive. you mind explaining just exactly what it is you want from the forum. 
[http://ubuntuforums.org/showthread.php?t=703541](http://ubuntuforums.org/showthread.php?t=703541)

---

### Post by bodhi.zazen on 2008-02-21
Try starting a thread with a more appropriate title.

	> AAAAAA I am sick of this!!!

	Is not a very descriptive title. Who wants to click on that title to see what it is about ???

	See this link.

	[http://ubuntuforums.org/showthread.php?t=700739](http://ubuntuforums.org/showthread.php?t=700739)

---

### Post by Afkpuz on 2008-02-21
Just a thought. If not booting from a usb drive, when you boot up, look for a message that says "Press so and so to enter setup".  Usually, its delete, or f2, or some other f key.  Press that button during boot up and get into bios.  There should be a setting somewhere in bios called "boot from usb".  If you're never going to install an OS on a usb stick, turning this setting off might help you get past this.  Then, your comp won't even look at your usb during the opening boot sequence.  I'm not sure if this is a sure-fire fix, but give it a try.


*EDIT* Also, please let us know if you installed ubuntu on your regular hard drive (internally) or on a USB hard drive.

---

### Post by wolfen69 on 2008-02-21
if you are dual booting, you need to make sure that the correct drive boots up first in BIOS.

---

### Post by rbc on 2008-02-21
Error 17 means the partition cannot be mounted becasue GRUB doesn't like the filesystem. Error 22 means the partition either simply isn't there, or it has been misnamed somewhere, and GRUB is looking in the wrong place for it. Please be more specific about how the hard drives and partitions are set up, internally, externally.

---

### Post by Jadd on 2008-02-21
AAAAAA I am sick of these titles!

---

### Post by Bigbluecat on 2008-02-21
OK.


The issue you have is that when you plug your USB drive in your are effectively changing the drive count and order as grub sees it.

The way grub works is that the boot record of your boot disk points to the drive and location of the file telling the system how to boot. Let's say for arguments sake that your boot drive is hd0. This may point to hd1 for the boot files.

I think what is happening when you plug in your usb drive is that it is enumerating as hd1 and probably your ubuntu drive is becoming hd2.

Hence when you try to boot like this the grub MBR tells the system to look on hd1 but this is now your usb drive and not your Ubuntu drive so you get error 17.

I don't know if there is a setting in your bios that you can change in order to ensure that your usb drive does not do this. Have a root around and look.

Else just continue to boot with the configuration grub expects. If you want to always boot with the usb drive plugged in you can re-write grub MBR with this configuration.

---

