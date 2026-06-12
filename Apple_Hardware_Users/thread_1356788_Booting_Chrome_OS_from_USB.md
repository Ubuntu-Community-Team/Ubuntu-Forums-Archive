---
title: "Booting Chrome OS from USB"
date: 2009-12-16
forum: Apple Hardware Users
---

### Post by besweeet on 2009-12-16
I was able to get Chrome OS onto a 1GB flash drive. It boots and works on 2 normal laptops that I tested on. I just want to get it to boot on my MBP without using a virtualization application.

My MBP currently triple boots with Windows 7 Pro x64, Snow Leopard 10.6.2, and Ubuntu 9.10 x64. All can be booted from via rEFIt (all three show up and boot just fine).

I've been playing around with the grub.cfg file from Ubuntu for the past few hours to try and see if I can edit it so that it can boot from the flash drive, but I can't get it to.

I added the following:
        insmod ext2 
        set root=(hd1,1)  
        linux   /boot/vmlinuz-2.6.30-chromeos-intel-menlow ro root=dev/sdb2 append quiet console=tty2 initrd=initrd.img init=/sbin/init rw 
        initrd  /boot/initrd.img-2.6.30-chromeos-intel-menlow 

The first error I got was "you must load the kernel first" or something like that. After a little bit of tweaking, it said "cannot get c/h/s values".

Any ideas? Just want to play around with Chrome OS without using VirtualBox or something (just don't care for virtualization or anything like that).

---

### Post by tom4everitt on 2009-12-21
Normally chrome should show up in rEFIt. 

In grub 2 you can always drop to shell by pressing c (when you have the boot options). Then you should be able to execute the commands from your grub.cfg. This will get you a little more information about where it goes wrong. After executing the linux /boot.... command for instance, it should tell you a kernel been loaded if succesful. Same with initrd command. 

You can also use
```
 
ls 

```
and 
```

ls (hd1,1)/ 

```

I have no idea what c/h/s values could be, if you want you can ask in their IRC channel, it's #grub at FreeNode.

---

### Post by besweeet on 2009-12-21
What exactly should I type in? I already put my grub.cfg back to normal. 

It shows up in rEFIt as a normal legacy drive, but when trying to boot from it, it just boots the non-Apple (Windows/Ubuntu) OS that I previously booted.

---

### Post by tom4everitt on 2009-12-22
Okay, that it shows up in rEFIt, but falls back to your normal boot indicates that it finds it, but then fails to boot it, so it falls back to your mbr boot... Not much to do about that I guess.

The commands I suggested was for booting it from grub2. When you reach your grub2 menu, you can instead of choosing to boot one of the options (such as your chrome os option) do it manually. 

I think you just press c, and then you should be able to execute the same commands as are in your grub.cfg entry. They don't need to be in the grub.cfg. 

What's happening when you choose to boot one option is that it executes all the commands that are in this entry in grub.cfg, but you can just as well do it in the shell directly. The advantage of doing it this way is that you will see exactly what's happening in each step. 

I wish I could give you a more exact answer on whats wrong and how to fix it... :)

---

### Post by besweeet on 2009-12-22
I went into the command-line interface for GRUB2:
```
sh:grub> set root=(hd2,2)
sh:grub> linux /boot/vmlinuz-2.6.30-chrome-os-intel-menlow root=/dev/sdc2
error: cannot get C/H/S values
```

So... Not sure what to do. People say it works with the original GRUB, but I don't know how to get that on here.

---

### Post by tom4everitt on 2009-12-23
Okay, so it's not even able to load the kernel... 

I think the C/H/S values its referring to are these:
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

which I guess indicates it has some trouble reading from the file system. Perhaps you need to run something like 'insmod ext2', depending on the file system the boot partition is...


What is the output of ls and ls (hd2,2)/ ?

---

### Post by besweeet on 2010-01-13
So I abandoned this little "mission", but I want to try again. This time, I'm going to try ChromeOS "Zero" made by Hexxeh: [http://chromeos.hexxeh.net/](http://chromeos.hexxeh.net/)

I was wondering if you could connect to my Ubuntu install and do the commands yourself? I think I'm doing something wrong... You seem like you know what to do, so maybe, to make everything simpler, we could have a pro do it :popcorn:.

---

### Post by besweeet on 2010-01-14
[SIZE="7"]OMG I DID IT!![/SIZE]

I followed this: [http://www.linuxquestions.org/questions/showthread.php?p=3794289#post3794289](http://www.linuxquestions.org/questions/showthread.php?p=3794289#post3794289)

I had to do linux16. I went into that, chose USB, and it worked! One thing: NO WIFI once I'm logged in.

---

### Post by wheredidrealitygo on 2010-01-14
You likely won't get wireless working, Macbook4,1 and after all have broadcom 4321 wireless chipsets IIRC, and according to the [Chromium OS dev hardware list]("http://sites.google.com/a/chromium.org/dev/chromium-os/getting-dev-hardware/dev-hardware-list") broadcom just isn't supported yet.

---

### Post by tom4everitt on 2010-01-14
> **besweeet said:**
> [SIZE="7"]OMG I DID IT!![/SIZE]


Congratulations! :)

---

### Post by besweeet on 2010-01-14
> **wheredidrealitygo said:**
> You likely won't get wireless working, Macbook4,1 and after all have broadcom 4321 wireless chipsets IIRC, and according to the [Chromium OS dev hardware list]("http://sites.google.com/a/chromium.org/dev/chromium-os/getting-dev-hardware/dev-hardware-list") broadcom just isn't supported yet.

Even if I install the drivers in Terminal in ChromeOS? Been trying to get it working, but I'm having problems with the PPA key and the ppa.launchpad.net/mactel-support repo. Trying to do the key stuff manually isn't working, since I can't seem to get a connection with keyserver.ubuntu.com.

---

