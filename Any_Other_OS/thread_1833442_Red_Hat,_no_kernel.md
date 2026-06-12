---
title: "Red Hat, no kernel"
date: 2011-08-26
forum: Any Other OS
---

### Post by GreenDance on 2011-08-26
Hi, I received an old Red Hat pc, but somehow it's missing it's kernel, is it possible to use a modern day distro to boot up the computer to install a kernel so I can get access to the hard drive.

Thank You.

---

### Post by boydrice on 2011-08-26
If you just want access to the hard drive just boot a live CD.

---

### Post by GreenDance on 2011-08-26
> **boydrice said:**
> If you just want access to the hard drive just boot a live CD.

I would like the system to be bootable, please.

---

### Post by boydrice on 2011-08-26
Ok, then I think you need to clarify your question.  Do you just want to access data on your hard drive, do you want to install a new linux distro, or do you want to make the current OS on your machine boot?  If it is question 1 then I have replied, if it is question 2 then tell me more about the machine and what type of OS you want on it, if it is question 3 then tell me what version of RH you are running and what type of errors or behavior you are seeing and why you think a kernel is missing as opposed to a hardware issue.  In short, help me help you.

---

### Post by cgroza on 2011-08-26
Boot a live CD. Mount your Red Hat partition and see if you can chroot into it.
If you can, installing the kernel should not be a pain using it's package manager.
You may have to update the grub configuration.

---

### Post by wojox on 2011-08-26
How old is old? Lilo old?

What error's do you get (just says "missing kernel")?

---

### Post by GreenDance on 2011-08-28
> **boydrice said:**
> Ok, then I think you need to clarify your question.  Do you just want to access data on your hard drive, do you want to install a new linux distro, or do you want to make the current OS on your machine boot?  If it is question 1 then I have replied, if it is question 2 then tell me more about the machine and what type of OS you want on it, if it is question 3 then tell me what version of RH you are running and what type of errors or behavior you are seeing and why you think a kernel is missing as opposed to a hardware issue.  In short, help me help you.

Hi, sorry for the late reply, when I turn the computer on, it passes the screen where it shows the hard drives then goes to another screen which is black with a white underscore blinking, all i know about the os is it's redhat from 10 to 12 years ago, sorry i don't know anymore about the version.

I would like to get this to boot please.

> **wojox said:**
> How old is old? Lilo old?

What error's do you get (just says "missing kernel")?

About 10 to 12 years old redhat, no error messages, on boot, after the boot process shows the hard drives connected, it goes to a black screen with a blinking underscore.


I know this is properly a long shot, but if it's possible to make this work I'd be most grateful. Thank You :)

---

### Post by GreenDance on 2011-08-29
It might be the bootloader that is missing :(

---

### Post by boydrice on 2011-08-29
So I am still confused, is your main goal to boot a 10+ year old distro or is it to retrieve data off the hard drive?

---

### Post by GreenDance on 2011-08-29
> **boydrice said:**
> So I am still confused, is your main goal to boot a 10+ year old distro or is it to retrieve data off the hard drive?

Boot the computer, please :)

---

### Post by CharlesA on 2011-08-29
IMHO, if you just want the machine to boot, try running a light new(er) distro instead of an ancient one. Lubuntu comes to mind but there are others.

---

### Post by GreenDance on 2011-08-29
> **CharlesA said:**
> IMHO, if you just want the machine to boot, try running a light new(er) distro instead of an ancient one. Lubuntu comes to mind but there are others.

Thanks, but the machine has data/programs on it, I really wanted to try to get it to boot.

---

### Post by cgroza on 2011-08-29
Have you tried chroot ing into it as I have said earlier?

---

### Post by GreenDance on 2011-08-29
> **cgroza said:**
> Have you tried chroot ing into it as I have said earlier?

How would I go about doing that please?

---

### Post by kk0sse54 on 2011-08-29
Sounds like you have no bootloader not a missing kernel, either way you'll have to use a liveCD to check that the partitions and data are correct and then chroot into the red hat installation in order to either install grub or lilo. 

As for the chroot using a liveCD, that's fairly easy

Find the partition you want using 
```
fdisk -l
```

Then create a directory and mount the partition
```
mkdir /mnt/redhat
mount /dev/sdaX /mnt/redhat
```

Mount some temporary filesystems
```

cd /mnt/redhat
mount -t proc proc proc/
mount -o bind /dev dev/
```

And finally chroot
```
chroot /mnt/redhat /bin/bash
```

Now you can either install a kernel or bootloader

*Note if there is a bootloader installed it's probably lilo in which case first check that the configuration file is right with 
```
nano /etc/lilo.conf
```

And then simply run lilo in order to install it in the MBR
```
/sbin/lilo
```

---

