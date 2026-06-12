---
title: "refit Triple Boot"
date: 2010-08-20
forum: Apple Hardware Users
---

### Post by dngfng on 2010-08-20
Hi,

I have recently triple booted my new MacBook Pro (6-2) with rEFIt.
First of I installed everything correctly got OSX, Win7 and Ubuntu to show up in the rEFIt bootloader. 

After I accidently destroyed Ubuntu I reinstalled it using the rEFIt bootloader on the same partition as the previous one. Everything works...

BUT

now I have two Linux Startup options in the rEFIt bootloader where I only shoud have one.

Before:
OSX Win Lin

Now:
OSX Win Lin Lin

Any Idea how I can get rid of the duplicate Linux entry?

Thanks in advanced.

I found this thread with a similar issue - but I am not sure if that solution would solve my problem:

[http://ubuntuforums.org/showthread.php?t=1198613](http://ubuntuforums.org/showthread.php?t=1198613)

> 
you'll need to run it using sudo:
 	Code:
 	sudo dd if=/dev/zero of=/dev/sda bs=440 count=1 



---

### Post by Old Codger on 2010-08-20
I had the same thing happen to me after I somehow managed to the install on two separate partitions, which I created by mistake during the install process. To fix the problem, I had to repartition the drive: i.e., one for Mac OS X and the other for Ubuntu and reinstall Ubuntu. If you check your partitions, you'll find that you have Ubuntu on two partition within the one you originally created for Ubuntu. You'll need to repartition and reinstall again to get rid of the second boot option. Good luck.

---

### Post by dngfng on 2010-08-20
What I did wrong:
On the first installation Ubuntu defaulted to install the Bootloader to the main Partition. For the second install I manually changed the location of the Bootloader to Ubuntu's partition (as I should have done the first time).

Now rEFIt found all four Bootloader's OSX, Windows, the original linux bootloader and the extra bootloader from the secondary installation.

By performing the command:

> 
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1 


I was able to delete the bootloader from the original installation.

Now when I start my Mac it only displays the 3 required Bootloaders.

---

