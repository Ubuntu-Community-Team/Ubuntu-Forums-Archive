---
title: "Can't Install Ubuntu 6.06"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Tom Scruffy on 2006-10-27
Hi guys, I'm new to Ubuntu.  I tried to install version 6.06 to a new (blank) hard drive, but it starts to do stuff and then it just goes to a blank screen with a curser at the top (pressing keys doesn't do anything).  To get it to restart I have to pull the power. If I try to start the install with safe graphics mode, it progresses farther but ends up with a command prompt that I don't know what to type. It is a Gateway PC with a 933 Mhz processor and a new 300 GB maxtor hard drive.  Do I have to set the partitions somehow? Anybody been there before?  Don't beat me up too bad, I'm not a computer whiz but I'm far from being completely stupid.  Any suggestions would be appreciated, 

Thanks Tom

---

### Post by tzulberti on 2006-10-27
You should try to download Ubuntu 6.10. 

Nevertheless, you could check if the cd was written correctly. I think that there is a option in the boot menu...

---

### Post by ratman99uk on 2006-10-27
I have the same with an old 700mhz pIII, 64mg ram, 20gb hd, tnt 2. 

I tryed using QTPARTED on a Knoppix disk to create a 1gb swap file partition and the rest ext3 in advance thinking the same however I still get the same result. So I don't think its the hard drive.

I noticed the live cd (i received two days ago) says that the machine requires 256mb ram to run which my machine dose not have. A friend at uni says you can get a non live CD version of the installer (Alternate install CD) that allows you to install on "systems with less than about 192MB of RAM."

[http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/ubuntu-6.06.1-alternate-i386.iso](http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/ubuntu-6.06.1-alternate-i386.iso)
(UK Server)

However I haven't tested this my self yet.

- Ratman99UK

---

### Post by rlozano on 2006-10-27
your friend is correct.

try to use the alternate install first and see if that will help you out. 1gb of swap file i think is too much. :-)

but nevertheless, keep us posted on your developments as we maybe able to help in the process.

btw, what video card do you have?

---

### Post by Tom Scruffy on 2006-10-27
My machine has over 256 Mb of RAM, so I don't think that is the problem for me.

---

### Post by steven8 on 2006-10-27
Do you get to the screen where it gives you the option to load or start ubuntu?

If you do, then choose the option to check the disk for errors.

---

### Post by Tom Scruffy on 2006-10-27
Yea, I checked the disc for errors and it said it was OK.  I tried to install it again but it does the same thing.

---

### Post by Tom Scruffy on 2006-10-27
I just tried to load it with the safe graphics mode and it told me after loading for a bit, that it didn't set up the X server correctly. The next sentence says that it is likely that it is not set up correctly and would I like to view the X server output to diagnose the problem? I'm not quite sure what I'm looking for though.

---

### Post by Tom Scruffy on 2006-10-27
The last few lines of the X server output said:

(EE) VESA

(EE) VESA(0): Cannot read V_BIOS
(EE) Screen(s) found, but none have a usable configuration

Fatal server error 

no screens found 

                         <OK>

Any thoughts anybody?

---

### Post by steven8 on 2006-10-27
I found this in another post about the x server.

Start the terminal and put in this code:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Tom Scruffy on 2006-10-27
That command worked and I had to answer a bunch of configuration questions, but then the screen went unresponsive when I answered the Attempt monitor autodetection? with a <Yes>:???:

---

### Post by steven8 on 2006-10-27
Oh boy.  I am a newbie as well, and this is already getting too deep.  What happens when you you reboot and try to come back into Ubuntu?

---

### Post by Tom Scruffy on 2006-10-28
I have to do the whole process all over again. Pressing no to the "Autodetect" monitor makes me answer a few more questions and then it gives me the same error "no screens found". I tried selecting a number of different drivers in the reconfigure mode but none of them worked.

---

### Post by steven8 on 2006-10-28
I did a search of no screens found.  It seems mostly tied to nvidia issues.  What kind of vid card do you have?  I didn't see where anyone solved it yet. :-(

---

### Post by steven8 on 2006-11-04
any luck?  I haven't found anything else.

---

### Post by harrysales on 2006-11-04
Have you tried the VGA option F4? across the bottom of the screen to select screen resolution before you install

---

