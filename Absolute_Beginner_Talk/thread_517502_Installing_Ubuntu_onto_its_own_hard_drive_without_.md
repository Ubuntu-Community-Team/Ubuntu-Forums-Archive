---
title: "Installing Ubuntu onto its own hard drive without dual boot"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by TheMudMan on 2007-08-04
The question I am posting is a little different than the common two hard drive-dual boot question: I do not want dual boot.  Dual booting whether on two hard drives or on a single hard drive just looks too complicated to set up, in adittion to being risky.

I really want to mess around with Ubuntu, but my family computer already has Win XP on it.  I do not want to fiddle with Win XP at all if possible.  

Would it be possible to purchase a new hard drive, unplug the original hard drive on my computer, plug in the new one, and then install Ubuntu on to that new hard drive?  Then when I am finished messing around on Ubuntu, could I unplug the new hard drive, plug in the orginal hard drive (with Win XP) and then turn on the computer and have it boot with Win XP, as if nothing had ever changed and with no possiblity of damaging the original hard drive with its files and OS?

If I ultimately find Ubuntu to be a great OS, then maybe I can just leave the new harddrive plugged in and never return to the orginal hard drive.  I find the dual boot idea nice but too complicated and risky. By the way, I have tried the Ubuntu 6.06.1 live CD and it works including the internet on my machine (Compaq Presario) so I assume that means Ubuntu recognizes all my hard ware.

Thank you.

To rehash, my aim is to use Ubuntu exclusively; I really am not interested in Windows, therefore I do not require dual booting, however this is my family computer and I myself would like to mess around with Ubuntu before removing Win XP completely from the computer.  So my plan is to swap entire hard drives by manuall plugging and unplugging them depending on which OS I want to use.  Is this posisble?

---

### Post by ron999 on 2007-08-04
Hi
What you are suggesting is possible.
Install Ubuntu on the new drive while the old drive is disconnected.

But there is another option.
On some motherboards it is possible to press F8 during bootup to take you to a mini-menu which asks you what device you wish to boot from.
If your motherboard has this function then you could have both drives connected and one set as default boot but be able to jump in quick to change the boot to the other drive if you want to use the other OS.
So have a look when your PC is starting up to see if it says 
'Press DEL for SETUP'  - most motherboards have this
and 
'Press F8 for BSS' - or something similar, that's the function I mean.

---

### Post by VChief on 2007-08-04
Yeah. That's very possible. You could also leave both installed. If you're hard drive cable isn't hooked up to anything other than your first hard drive, you can hook both up. Just let Ubuntu install GRUB, then you can dual-boot with two separate hard drives. If you don't want to hurt the XP drive's master boot record, you can put the Ubuntu drive as the master drive and XP as the slave. That's how my system is setup. Ubuntu has it's own hard drive (master) and my slave drive is a combination of XP and whatever distro I'm "testing out."

---

### Post by benx009 on 2007-08-04
> **TheMudMan said:**
> The question I am posting is a little different than the common two hard drive-dual boot question: I do not want dual boot.  Dual booting whether on two hard drives or on a single hard drive just looks too complicated to set up, in adittion to being risky.

I really want to mess around with Ubuntu, but my family computer already has Win XP on it.  I do not want to fiddle with Win XP at all if possible.  

Would it be possible to purchase a new hard drive, unplug the original hard drive on my computer, plug in the new one, and then install Ubuntu on to that new hard drive?  Then when I am finished messing around on Ubuntu, could I unplug the new hard drive, plug in the orginal hard drive (with Win XP) and then turn on the computer and have it boot with Win XP, as if nothing had ever changed and with no possiblity of damaging the original hard drive with its files and OS?

If I ultimately find Ubuntu to be a great OS, then maybe I can just leave the new harddrive plugged in and never return to the orginal hard drive.  I find the dual boot idea nice but too complicated and risky. By the way, I have tried the Ubuntu 6.06.1 live CD and it works including the internet on my machine (Compaq Presario) so I assume that means Ubuntu recognizes all my hard ware.

Thank you.

To rehash, my aim is to use Ubuntu exclusively; I really am not interested in Windows, therefore I do not require dual booting, however this is my family computer and I myself would like to mess around with Ubuntu before removing Win XP completely from the computer.  So my plan is to swap entire hard drives by manuall plugging and unplugging them depending on which OS I want to use.  Is this posisble?

yes, what you are saying is possible, but if we're talking about internal hard drives here, wouldn't you be taking a bigger risk at damaging your system by "plugging and unplugging them" than by just setting up your system to dual-boot?

---

### Post by Grovers on 2007-08-04
I'm still new to Ubuntu but I don't see a problem in doing that. To me that seems like alot of unnecessary work though. 

When I installed Ubuntu it did all the partitioning for me. I use two hard drives and I got to choose which one I wanted it installed on. As long as you know which is the new one you can make that one just for Ubuntu. It also set up my dual boot without any problems. 

So if you want to keep pulling out the hard drive just to switch between the two go ahead but Ubuntu will pretty much do all the work for you. The only thing with mine is, I have to pay attention if I want to use Windows because if I don't select which one I want, it goes directly to Ubuntu.

---

### Post by VChief on 2007-08-04
> **benx009 said:**
> yes, what you are saying is possible, but if we're talking about internal hard drives here, wouldn't you be taking a bigger risk at damaging your system by "plugging and unplugging them" than by just setting up your system to dual-boot?

That's true. Everytime you would plug and unplug your taking risks of bending pins, etc...

---

### Post by wolfen69 on 2007-08-04
what you want is how i have mine. unplug the xp drive, install ubuntu to the new. then you can connect both and choose which one to boot to in the bios, or you may have quick boot option such as f12 to choose which drive to boot to. dont worry, it wont hurt your xp drive at all. you dont need to keep unplugging and plugging in.

---

### Post by russell.h on 2007-08-04
Thats exactly how I did mine originally. At some point though I plugged the XP drive back in, and now I dual boot. I forget if I had to do something to make grub see the XP drive, that was over a year ago now.

But anyway, dual booting really isn't complicated. It is different than using a single hard drive in only 2 ways to the user:

1. During install you have to tell Ubuntu not to overwrite windows (in your case just tell it to go on the other drive, if you only had one you would tell it to shrink the windows partition)

2. During boot up a screen comes up asking you which OS you want to use. It will probably start with Ubuntu selected and count down from 10 or 20, so if you just ignore it then it will boot Ubuntu normally. At any rate you can fairly easily configure the boot menu (I was able to explain to my 12 year old sister how to do it over the phone) to appear in any order you want, and with any countdown you want (or no countdown if you prefer).

Other than that there is nothing to it. I think the latest versions of Ubuntu (not sure how recent) will automatically mount your XP drive(s) if you had them connected during installation, so if you want to access files from XP then its simply a matter of opening up the drive and finding the file.

---

### Post by xmastree on 2007-08-04
Hmm... if you do this, and install ubuntu on the disk when it is primary master, then try to boot from it as primary slave, I don't think it'll work as the fstab will be looking for partitions on /dev/hda when they're now on hdb...

---

### Post by VChief on 2007-08-04
> **russell.h said:**
> Thats exactly how I did mine originally. At some point though I plugged the XP drive back in, and now I dual boot. I forget if I had to do something to make grub see the XP drive, that was over a year ago now..

Shouldn't be a problem. Wasn't for me. GRUB not only saw the drive, but also configured it so that XP will think it's the master drive.

---

### Post by oilchangeguy on 2007-08-04
that's how i dual boot. using two drives. set the jumpers on the ubuntu drive to master (install it as master), and set the windows drive to slave. plug everything back in and grub should add windows to the list. then you can select from ubuntu or windows.

---

### Post by TheMudMan on 2007-08-09
Thanks for all the replies, they are very helpful.

I have now installed Ubuntu onto an old hardrive which I switched with my current hard drive.  It is a great way to try out new operating systems.

---

