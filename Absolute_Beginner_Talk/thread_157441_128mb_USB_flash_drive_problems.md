---
title: "128mb USB flash drive problems"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by LostinLinux on 2006-04-09
Hi :)

I have ubuntu working really well at the moment, absolutely love it!

However, trying to use my usb flash drive with it, but its a no go. First of all, i have tried mounting it manually, but the problem is, my /dev/ directory just doesnt contain an appropriate device file. Reading through most posts i see that most people point to:

sda0
sda1

or

sdc0
sdc1

None of those files exist on my notebook :( :confused: 

So if i add the correct commands in /etc/fstab it makes no difference as those files cannot be located. 

Any help?

best.

---

### Post by Mustard on 2006-04-09
With the device plugged in, enter this command below in terminal and paste the output in here...

```
sudo fdisk -l
#lists all partitions that linux can see
```

---

### Post by LostinLinux on 2006-04-09
Disk / dev/hda: 6007 MB, 6007357440 bytes
255 heads, 63 sectors/track, 730 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot         Start            End             Blocks       Id    System
/dev/hda1     *               1            696            5590588+   83   Linux
/dev/hda2                  697            730              273105      5    Extended
/dev/hda5                  697            730              272073     82   Linux swap / Solaris

Hope this is correct? The usb stick is plugged in, but still nothing :( Any ideas. 

The stick works fine with WinXp and Mac OSX Tiger...

---

### Post by Mustard on 2006-04-09
It would seem that linux is not seeing it at all.  Why that is the case I am not sure. 

Is it being plugged in via a built in USB port or via a USB hub?
If it is via a hub, is it a powered hub?

It might be worth looking through the logs in the /var/log/ folder to see if there are any indications of it being detected and any errors showing why that was unsuccesful.

I'm not sure whether this is the right log to look at, but try this command..

```
dmesg | less
```

In gnome you can view system logs from the Applications>>System Tools>>System Logs menu choice as well.

---

### Post by LostinLinux on 2006-04-09
hmm, no it doesnt appear it is detected. Its very strange. 

The ports are built into the notebook and i know they function correctly as i had winxp installed on it before ubuntu and it worked fine.

Maybe someone could send me their usb device files?

Or mabe i should try a reinstall?

---

### Post by Mustard on 2006-04-09
[QUOTE=LostinLinux]hmm, no it doesnt appear it is detected. Its very strange. 

The ports are built into the notebook and i know they function correctly as i had winxp installed on it before ubuntu and it worked fine.

Maybe someone could send me their usb device files?

Or mabe i should try a reinstall?[/QUOTE]

A reinstall would be a drastic and possibly fruitless exercise, so I would say its a bit early to take that route.

I would continue to attempt to troubleshoot the issue via the system logs.  You can paste any messages you find that might be relevant to the USB drive being detected that you find in the logs in this thread and others may be able to work out what is going on.

---

### Post by LostinLinux on 2006-04-09
ok, just had a look at my syslog and it clearly recognises my USB ports and detects them.

But i dont see what i can find from logs, surely the problem is that the device file doesnt exist on my notebook? Or am i not understanding something...

---

### Post by chettyk on 2006-04-09
A suggestion. Perhaps you could consider reformating the USB stick and then trying it out again.

---

### Post by Bloch on 2006-04-09
I had a Gateway 128MB mp3 player / memory stick and tried to use it with linux kernel 2.4 (I was using the Libranet distro then) 
After long efforts I found that it was not compatible. I found on the web some notes by the person who wrote the linux driver for these types of devices! The basic problem is that some cheap brands of hardware devices are tested solely with windows. They are not tested to ensure they comply with the international standards for these type of devices. 
Do an internet search and if many people are having problems, it might be better to accept that you will not be able to get it to work - or perhaps only get it to work at the risk of breaking your system.

---

### Post by LostinLinux on 2006-04-09
Reformmating didnt help :(

I understand about compatibility issues, however, i dont think that is my problem.

There are no sda device files on my notebook, so it will never work. I think i need those files before i can go any further...

---

### Post by chettyk on 2006-04-09
[QUOTE=LostinLinux]
There are no sda device files on my notebook, so it will never work. I think i need those files before i can go any further...[/QUOTE]

It is difficult to understand how sda devices files were not included during install. I have done fresh installs with Ubuntu 5.04, 5.10 and Dapper Drake, and I have never had that happen.

Have you tried plugging in another USB device, such as another USB key (preferably one known to be working with Linux) or perhaps an electronic camera, and seeing if that is detected? Maybe you could also consider trying your USB key with another Linux system and checking what happens.

---

