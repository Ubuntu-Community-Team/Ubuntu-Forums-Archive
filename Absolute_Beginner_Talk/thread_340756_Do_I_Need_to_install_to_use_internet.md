---
title: "Do I Need to install to use internet"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by LuckysCharms on 2007-01-17
Okay, so I have a 64bit system but the 64bit version of 6.10 didn't work AT ALL. So I downloaded the 6.06 i386 version. It loaded great. But I have no use of the internet or of my personal files. I had used Knoppix Live CD and had access to all my drives. So my question is do I absolutely need to install Ubuntu in order to access my drive and use the internet? and is there a safe way of making this a dual platform system untill I get used to the linux system?

---

### Post by thornomad on 2007-01-17
You shouldn't need to install from the LiveCD to access the internet.

I am not sure, however, about accessing files on the physical hard drive once you have booted to a LiveCD.  Someone else probably knows though ...

---

### Post by LuckysCharms on 2007-01-17
OKay, well could the fact that I'm using a wireless network limit me from using the internet

---

### Post by meng on 2007-01-17
It depends if your wireless card is detected by the LiveCD. If it is, then you just need to configure it. Look under System > Admin > Networking and describe what you see.

If you have enough disk space, you should defrag your drive with Windows disk defragger and install Ubuntu and dual-boot. It's pretty safe, but you are recommended to back up just in case an unexpected catastrophe occurs. Otherwise you can continue to boot from the Live CD, and there is a method of saving your data/settings to a USB drive. Search the forums for "persistent USB" or "persistent home".

---

### Post by jd65pl on 2007-01-17
[LIST=1]
[*]You can dual boot by using the standard installer provided on the live cd
[*]Dependent on your wireless card you may need some configuration for it to work, check this site to find out about its compatability [http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)
[*]You can mount you hard disk drive using the command below. For mounting ntfs see this link [https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28ntfs%]("https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28ntfs%29")29[/LIST]
```
sudo mount /dev/hd## /*moutpoint*
```

---

