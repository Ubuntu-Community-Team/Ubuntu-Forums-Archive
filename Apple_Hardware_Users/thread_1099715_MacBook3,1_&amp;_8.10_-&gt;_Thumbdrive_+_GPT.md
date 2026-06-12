---
title: "MacBook3,1 &amp; 8.10 -&gt; Thumbdrive + GPT"
date: 2009-03-18
forum: Apple Hardware Users
---

### Post by stuartbh on 2009-03-18
ALCON:

I have never (not even back when I had a PC) tried to make a bootable USB flash drive type installation of Linux. I have been doing data recovery lately, and wanted to find out what would be the right way to go about this.

Now, to me, size does NOT matter, my preference would be to have as full boat of a Linux system as possible leaving nothing out, I am not looking to go "small" since these USB sticks are so inexpensive these days for large GB sizes, and I am okay to buy a larger sized flash stick.

Of course my first go at this would be with Ubuntu 8.10, though I would be as well interested to know if this process could be repeated to make a CentOS type of stick also.

I have zero care as to if this is compatible with a PC, I only care to make it work with Macs, that's all I need. So using things like GPT, HFS+ and that are fine by me.


Stuart

---

### Post by Unix-Man on 2009-03-18
Well once i tried booting 7.10 off a 4GB thumb drive and the installer got to 98% then said it couldn't install yaboot the device is unbootable.

I didn't really understand file systems at the time so you might be able to format the drive to EXT3 and it's very possible it will work. So just boot off the live CD go to System>Administrator>Partition Editor inside the partition editor (Make sure your Thumb Drive is plugged in) select the thumb drive right click on it 
and im pretty sure you can change the format to whatever you want. Then run the installer on the desktop and select the thumb drive and install.        

let me know what it says if you get errors because you might have the same problem i had

---

### Post by cyberdork33 on 2009-03-18
> **stuartbh said:**
> ALCON:

I have never (not even back when I had a PC) tried to make a bootable USB flash drive type installation of Linux. I have been doing data recovery lately, and wanted to find out what would be the right way to go about this.

Now, to me, size does NOT matter, my preference would be to have as full boat of a Linux system as possible leaving nothing out, I am not looking to go "small" since these USB sticks are so inexpensive these days for large GB sizes, and I am okay to buy a larger sized flash stick.

Of course my first go at this would be with Ubuntu 8.10, though I would be as well interested to know if this process could be repeated to make a CentOS type of stick also.

I have zero care as to if this is compatible with a PC, I only care to make it work with Macs, that's all I need. So using things like GPT, HFS+ and that are fine by me.


Stuart
have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

---

