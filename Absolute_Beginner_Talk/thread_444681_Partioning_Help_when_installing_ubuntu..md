---
title: "Partioning Help when installing ubuntu."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-05-15
Greetings,
I am trying to install ubuntu on another computer, of which *had* ubuntu on it before, but messed something up with the grub menu.lst file, I think, and we had to reinstall Windows and erased the partion that the installer created.

Well, the partion still exsists, but nothing is on it.
I am in the installation, and at the partioning section.

Here are two screenshots. (At the bottom of the post)
If you could look at them, and then try and help me figure out what I am to do, I would appreciate it, as I don't understand what I am trying to do.

---

### Post by rich.bradshaw on 2007-05-15
I guess you are trying to dual boot with Windows.

I guess that Windows is the 78GB drive on sda1.

I guess that you want Linux on the rest of the drive.

If any of this is wrong, don't do what I say next.






Ok.

Delete everything except sda1.

Make

10 GB ext3 for /
512 MB swap for swap

Make the rest ext3 for /home

install Ubuntu to /.

That's it.

You can adjust those amounts as you choose. Remember that all software goes into /, and all your data and settings goes into /home. /home should be bigger than /. 10GB is enough for / by far - I only have 5 GB for / and /home together.

This way you can reinstall Ubuntu on / without having to erase your home directory, meaning future upgrades will be painless.

---

### Post by Dr Small on 2007-05-15
Ok. You are on the money so far.
Here is another screenshot. Please make sure I have everything correct, I don't want to make a mistake :)

Dr Small

---

### Post by indytim on 2007-05-15
If you don't have anything beyond sda1, I'd suggest deleting the partitions you set up.  Once deleted, create 1 extended partition for all of the unallocated space on the hd.  Once the extended partition has been created, then within that partition, create your ext3, swap & FAT32 partitions.  Leave room for any additional partitions you may want to add later if it applies.  With this approach, you can easily add partitons later without going into "partitions lock" because you are trying to exceed 4 primary partitions.

Been there, done that (and it is a real pain-in-the-.....) to fix

Good Luck,

IndyTim

---

### Post by mikewhatever on 2007-05-15
All is correct, but now you have four primary partitions, so you won't be able to create another one. Are you planning to use the unallocated space? If so, delete the partitions for Ubuntu, create an extended partition of about 11 GB, then create root and swap as logical partitions within the extended one. The reason for doing this is because you there is a limit of 4 primary partitions per hdd.

---

### Post by Dr Small on 2007-05-15
Ok. Thanks for the help guys.
Here is a screenshot of the next setup page that I have now.
Please tell me if all information is correct.

Dr Small

---

### Post by mikewhatever on 2007-05-15
Yes, the mount points are good.

---

