---
title: "Need some help, ubuntu cant see any hd partitions!"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Tekkz on 2007-11-02
Hello everyone, I'm a fairly new ubuntu user and I'm having some troubles with a dual boot installation on my new system. I can boot from the liveCD(7.10) just fine, however during the installation process it cannot detect any partitions anywhere on my system. I have already created 30gb of unallocated space to install ubuntu with, however it cannot detect ANY hard drive partitions whatsoever, not even the current windows install. It's as though the hard drive doesn't even exist.

It should probably be said that I have no special setups on this machine(RAID, etc.), It's just a standard 250GB Western-Digital OEM hard drive, can anyone help me and explain why it wouldn't be able to detect these partitions?

Thanks in advance.

---

### Post by taurus on 2007-11-02
While still in the LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by Pumalite on 2007-11-02
You can use Gparted Live CD and prepare drive before installation:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
A good scheme is:

10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for /home

---

### Post by Tekkz on 2007-11-02
Thanks for the quick replies!

@taurus
The output of that command returns nothing, it simply puts me back at the prompt.
Heres a picture if it helps you understand my problem:
[IMG]http://i218.photobucket.com/albums/cc129/tekkvicious_photo/Screenshot.png[/IMG]

@Pumalite
I'll try that, thanks!

---

### Post by Tekkz on 2007-11-02
Alright just tried Gparted livecd, it's not reading anything either. Is there anything else I can do?

---

### Post by Tekkz on 2007-11-02
shameless bump

---

### Post by Pumalite on 2007-11-02
Try rescuecd: [http://www.sysresccd.org/Download.en.php](http://www.sysresccd.org/Download.en.php)
It has a partitioner.

---

