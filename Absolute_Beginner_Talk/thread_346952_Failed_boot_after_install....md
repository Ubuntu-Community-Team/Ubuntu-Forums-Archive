---
title: "Failed boot after install..."
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by roc4fun on 2007-01-26
Hi All,  this is a new system with only 6.1.0 installed.  

sda1 1st partition - 50G /
sda1 2nd partition - 4G swap
sda1 3rd partition - 100g home

my install seemed to do fine, but when I boot from the hdd I get lots of text ending with 'waiting for root filesystem' and nothing else happens.

Any ideas?

---

### Post by citizenofnowhere on 2007-01-26
I had this happen to me a while back. But this was on Dapper (6.05),  not Edgy. 

When you first boot up and get into the grub menu, which kernel version does it tell you you have?

---

### Post by roc4fun on 2007-01-26
I'm given 3 choices...

The generic kernel, the generic kernel recovery mode, and somthing about memtest.

It defaults to using the generic kernel.

Then there is lots of text ending with 'waiting for root filesystem'

Is it possible during my install I didn't put to root files in the right partition?

---

### Post by citizenofnowhere on 2007-01-26
What you have is a documented bug (see here: [http://ubuntuforums.org/showthread.php?t=282956](http://ubuntuforums.org/showthread.php?t=282956))

Unfortunately, these people had another kernel to pick from to boot into. Let's see...

Do you have a Dapper cd lying around anywhere (6.05)? I'm thinking since this is a fresh install, it's possible to install with Dapper then upgrade to edgy using the Edgy CD - only a little longer. That should allow you to pick the kernel and run any neccessary fixes mentioned in the thread. I can walk you through it

---

### Post by roc4fun on 2007-01-26
I don't have another install cd; I'm posting using the Livecd.

Would it be possible to 'apt-get' another kernel?  

What about these scripts?

Try to update the initramfs scripts for both kernels thanks to these commands :
Code:

sudo update-initramfs -u -k 2.6.17-10-generic 
sudo update-initramfs -u -k 2.6.17-10-386

I got this from the thread you quoted.

---

### Post by citizenofnowhere on 2007-01-26
The problem is the livecd won't make any changes to your existing installation. So running the commands off the livecd will not have any lasting effect. 

The fact that the livecd boots up is interesting though. That means that theoretically everything should work. (I'm also running on the generic kernel).

Maybe it was a bad installation? Are you willing to try installing again just to be certain?

---

### Post by citizenofnowhere on 2007-01-26
Before you reinstall here is what you can try with your livecd (as sudo).

```

mkdir /mnt/ubuntu
mount /dev/hda1 /mnt/ubuntu
chroot /mnt/ubuntu /bin/bash

```

that will make the livecd use your installated ubuntu as your default system.

Then run

```

sudo apt-get update
sudo apt-get install udev
sudo update-initramfs -u -k 2.6.17-10-generic
reboot

```

You can also add to be sure, but should work without these:

```

sudo update-grub
sudo aptitude reinstall linux-restricted-modules-2.6.17-10-generic

```

One of these should definitely fix things.

---

### Post by roc4fun on 2007-01-26
Well, lots of updating occured after using those commands, and I saw things were being written to the hdd.  

I hope I did the correct thing, but in this statement...

"mount /dev/hda1 /mnt/ubuntu"

I substituted sda1 for hda1 because my hdd is sata.

When I rebooted it was still the same, lots of text then waiting for root filesystem.

I'm convinced I'm using the generic kernel from the livecd and it's working.

---

### Post by roc4fun on 2007-01-26
Here is some more info...

I went through the above procedure again to confirm and when I got to the update-grub step this was the output...

root@ubuntu:/# sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=06ac53f6-da93-4a4b-97f1-6410816f161d'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Does this indicate there is some confusion about where some files are located?

Hope this helps.

---

### Post by citizenofnowhere on 2007-01-26
:( 

Anyone else out there got any ideas?

I've got a thread sitting here that could help, but the instructions are so long it doesn't seem worth it.

My advice (sorry ubuntu dudes): download either [Linux Mint ]("http://linuxmint.com/download.html")(get the "barbara" version - the one i'm using - it's an edgy spinoff, it comes with all the non-free audio/video/flash stuff preinstalled and a blue theme but thats about all the difference)  

OR the new PCLinuxOS. The new beta has a few unstable things, BUT it comes with nice beryl eye candy preinstalled, one of the easiest interfaces ever, great driver support and a stable kernel that should boot up on your system. It's also very pretty and I've had good experiences with the forums.

[http://www.pclinuxos.com/news.php](http://www.pclinuxos.com/news.php)

Don't give up on Ubuntu, but that kernel thing is a pain. I'm not sure it's worth the time.

---

