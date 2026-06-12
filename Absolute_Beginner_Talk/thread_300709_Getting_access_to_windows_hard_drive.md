---
title: "Getting access to windows hard drive"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by bradasmaximus on 2006-11-16
I have Windows on one hard drive and Ubuntu on the other,can anyone please tell me how i can i access the windows one so i can listen to my music and watch videos.

---

### Post by Gaweph on 2006-11-16
There are probably a lot of threads that solve this, it is a very common question.  But here is a quick answer:

The file you are looking to edit is:

/etc/fstab

so you can open up the terminal and do: 

sudo gedit /etc/fstab

you will see a list of files that are mounted aty startup.  you want to add your drive to the list:

for an NTFS drive, add:

/dev/hda1    /media/Windows ntfs  nls=utf8,umask=0222 0    0

fot Fat32 do this:

/dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0

the important part is the hda1, this is the drive and partition your using.  so it might be, hdb1 or hda2 or something, youl have to work that out.  Since you said windows was on the second Harddrive, im guessing it will be hdb1!

by mounting the things in /media, they will appear on the desktop.

Hope this quick guide helps you out

---

### Post by bradasmaximus on 2006-11-16
Thanks mate worked great.

---

### Post by jaboua on 2006-11-16
If you should want to write to NTFS partitions too some time in the future, you should check out ntfs-3g - if you search the forums, I believe there are some threads about it.

---

### Post by bradasmaximus on 2006-11-16
Ok thanks that will come in handy.

---

### Post by hyper_ch on 2006-11-16
The ntfs-write thing is still considered experimental - this means you could f*** up your ntfs partition and loose all data. Be carefull about that.

---

### Post by David Marrs on 2006-11-16
> **sjau said:**
> The ntfs-write thing is still considered experimental - this means you could f*** up your ntfs partition and loose all data. Be carefull about that.
I know people who've had no problem with ntfs-write. If you've not got important data on there it's probably worth the risk for the convenience gained. It's certainly not something I'd do though, as my windows partition is purely for work and the cost of reinstalling my system and data is something I'd rather avoid.

---

### Post by jaboua on 2006-11-16
> **sjau said:**
> The ntfs-write thing is still considered experimental - this means you could f*** up your ntfs partition and loose all data. Be carefull about that.The kernel driver is safe, but only supports overwriting files without changing the filesize... The dangerous driver was moved out of the kernel a long time ago. Maybe you speak of some third-party driver...

About the alternatives...
Ntfs-3g is a relatively new third party ntfs-driver, and is supposed to be perfectly safe.

Captive-NTFS will allow you to use Microsoft's own NTFS drivers.

I never got captive ntfs to work, but ntfs-3g has worked like a dream.

---

### Post by Tri_X_Troll on 2006-11-16
fat32 would be safe to write to, correct?

---

### Post by hyper_ch on 2006-11-17
fat32 is no problem to write to :) you don't even need to install anything additional

You should even be able to auto-mount it from the disks menu in the system/administration part of k/ubuntu...

---

