---
title: "Boot failures on Asus X79 Motherboard"
date: 2012-05-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by stubbs4 on 2012-05-28
I have an ASUS X79 mother board, Intel i7 processor,  32 gig of RAM qty 2- 1 tb drives, and a GeForce N460GT video card.

ubuntu 12.04 and 11.04 fail to boot from either the livecd or the memory stick.
ubuntu 10.04 boots from both, but there is no network or sound.
All 32 bit versions.

I'll photograph the display tomorrow and post the actual failure points, unless someone has something they can tell me now????


Glenn

---

### Post by journeyman01 on 2012-05-29
I have a similar problem.  I just got a P9X79 Pro motherboard with a 3930K processor.  I was able to install 12.04 64-bit fine from a USB stick, but once I restart I encounter problems.  

Ubuntu loads and allows me to enter my password.  Then the OS starts and loads the dash, but quickly freezes and becomes unresponsive to mouse or keyboard.  

The Q-Code on the motherboard display shows 3C, which is "post-memory PCH initialization is started".  Not sure what that means.  

Other components on this new build are:
Asus P9X79 Pro motherboard
Intel Core i7 3930K
Corsair Hydro H80
GSkill DDR3 1866 32 GB (8x 4GB)
Asus HD6570 graphics card
Western Digital Caviar Black 1TB (plugged into a SATA 3Gb port)

All suggestions welcome!

---

### Post by stubbs4 on 2012-05-29
You got a lot farther than I did. I put the LiveCD in, it blinks at me, then nothing.
 
Glenn

---

### Post by kitchenguy on 2012-08-12
Need some help here please!

Same thing here, 64 Bit Live CD or USB will not boot, I see a flash of the Ubunutu purple screen and then it hangs with a flashing cursor.

I have a different MB, my new rig is a Gigabyte GA-X79-UD3 with I7-3820 and 8GB of 2133 DDR3 with Gigabyte GTX550 TI and a Samsung SSD.

I have done more than 50 installs of Linux since 2007, so I would have thought I had got the hang of it by now.

Figure it is either the graphics card or the MB or the chip.  Going to try Kubuntu, PC Linux OS and Suse tonight to see if they will work, but I really would prefer to stay with Ubuntu, especially since I finally got used to the vertical dock bar (still don't like it or the fact that I can't put it at the bottom where it should be, but I am used to it now)

---

### Post by kitchenguy on 2012-08-12
Sorry, just noticed this is ASUS support.  My PC has gigabyte stuff in it.  However since it is the same issue with the same chipset (X79), I figure it is not manufacturer related.  I posted a new thread in Install/Upgrade problems area:

[http://ubuntuforums.org/showthread.php?p=12168076#post12168076](http://ubuntuforums.org/showthread.php?p=12168076#post12168076)

---

### Post by stubbs4 on 2012-08-12
Just a follow up.
I was never able to get Ubuntu or any other Linux build to install and run on my particular combination.
I ended up installing Windows server on it, which works fine (OK, as fine as it's possible for anything Microsoft to run)
 
Glenn

---

### Post by kitchenguy on 2012-08-14
Hi Stubbs4.  I found a solution for me at [http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383) talks about how to install in UEFI mode.
 
I also got a bit further by:
 
1. Going into my boot options and specifically choosing the DVD drive to boot from
2. hitting any key quite fast and continually until the Ubuntu grub screen comes up
3. press F6 to bring up options
4. Set ACPI=OFF
 
Not a solution if you want ACPI, but it worked to get it to boot, so maybe it will help you get further as well.  I am now going back to install all in UEFI mode.
 
Ho hum, yet another FDISK for me...

---

