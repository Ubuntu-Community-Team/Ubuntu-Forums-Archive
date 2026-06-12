---
title: "Installed wrong type of Ubuntu?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Firequacker on 2007-08-18
I downloaded and installed Ubuntu, the 64 bit version, and was told that the other versions are much more widely supported and that I should switch. How do I uninstall Ubuntu, and everything I've downloaded on it's little partition, but keep the partition in place so I can just switch to the other version. Is there an easy way to switch without going through all of this? Any extra advice would be GREATLY appreciated.

---

### Post by jd65pl on 2007-08-18
Any particual reason you would like to get rid of the 64bit version? If everything is working for you then why change? The only problem I have ever had with 64bit is a 64 bit version of flash, but other than that I have had nothing but success with it. I'm sure others have had a different experience though. If you've had any difficulties or problems maybe the forums could provide a solution.

If you want to start again with a 32bit system I would probably just download an image for the version you want burn it to disk and let the installer take care of everything else.

---

### Post by Firequacker on 2007-08-18
Well I couldn't download and install flash for it and there some other programs that weren't compatible, and an official source told me there are less things supported in that version... and I REALLY need flash, I've been developing in it for years. So if I run the installer it won't have to make a new partition? Will it delete the info thats already on there for me so I don't have to?

---

### Post by jd65pl on 2007-08-18
The installer should give you an option to delete or over write your existing Ubuntu partition. See [this ]("http://www.psychocats.net/ubuntu/installing")on installing there are also lots of other sources such as the forums or the [ubuntu wiki]("https://wiki.ubuntu.com/")

---

### Post by Hospadar on 2007-08-18
The easiest way I think would be to delete the old partitions that you had ubuntu installed on, and then use that free space to make new partitions

---

### Post by kwacka on 2007-08-18
There's an install script for installing flash on a 64 bit box at: 

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

Check out the X86 64-bit forum here.

If you really want 32bit ubuntu it's a doddle to install if you've got a separate /home partition, just burn the CD and select manual partitioning when asked.

---

### Post by Firequacker on 2007-08-18
What's the difference between the two types besides the software compatibility issues I'm having, anyways?

---

### Post by jd65pl on 2007-08-18
Ones for a 32 bit architecture and one is for a 64 bit architecture i.e. one operating system is designed for 64 bit processors the other for 32 bit. [Here]("http://www.softwaretipsandtricks.com/windowsxp/articles/581/1/The-difference-between-64-and-32-bit-processors") is something on the difference between 32 bit and 64 bit processors.

---

### Post by Paul133 on 2007-08-18
Most people will be just fine with the 32-bit OS, and it is much better supported. I have a dual-core 64-bit processor and I still use it. In order to ge tthe 32 bit OS you'll have to download the 32-bit .iso and burn it to diskl as an image (just liek you did with the 64-bit iso). Then set BIOS to boot from the disk, put in the LiveCD, and install it. If you manually partition, you should be able to format the partiton UBuntu is on now and install the 32-bit OS instead.

---

