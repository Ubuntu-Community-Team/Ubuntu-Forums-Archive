---
title: "processor for ubuntu"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by ros060 on 2006-03-17
i was just curious if and amd 450 mhz would be enough to run ubuntu?
and is there any application in ubuntu to list the hardware components of the machine it is running on. something like cpu z? 
cheers

---

### Post by rfruth on 2006-03-17
Its gonna be s l o w, how much memory is there ?  lshw shows lots of info, here is mine [http://www.rfruth.net/resume/computers/breezy/breezylshw.txt]("http://www.rfruth.net/resume/computers/breezy/breezylshw.txt")

---

### Post by souteneur3190 on 2006-03-17
yah, ive seen wors run on ubuntu but i would try xfce instead of gnome.

yah rfruth is very right, its a lot of frustration... Solaris 8 would be a better choice, lol.

---

### Post by steve.horsley on 2006-03-18
lshw seems to discover more if it runs with root privilege:
sudo lshw

But beware - **sudo lshw | less** can be very irritating because less gobbles the password prompt from sudo. You need to sudo something first to prime it so that it doesn't ask for the password again (if that makes sense).

---

### Post by Bartender on 2006-03-18
ros -
The PC described in my sig works fine with standard Ubuntu install.  I mean, it takes a second when I ask the PC to do something new, and System Monitor shows CPU utilization spike to 100% frequently, but it works just fine.  Doesn't crash or act flaky.

---

### Post by Perfect Storm on 2006-03-18
Aye, but you have alot of ram ^^ and gnome are more depending on ram than Proccessor.

---

### Post by dbott67 on 2006-03-18
[QUOTE=ros060]i was just curious if and amd 450 mhz would be enough to run ubuntu?
and is there any application in ubuntu to list the hardware components of the machine it is running on. something like cpu z? 
cheers[/QUOTE]

I'm running Ubuntu (w/ Gnome DE) on a PII-300 MHz with 256 MB RAM.  The system is a little sluggish, but is quite functional.  I've tried most desktop environments and window managers, but keep coming back to Gnome.  I'm willing to sacrifice a little performance for functionality and intuitiveness (as it pertains to me).

With respect to the various desktop environments, although XFCE and blackbox/fluxbox are lighter weight and appear to be "snappier" than KDE or Gnome, I find that the choice of application (Opera vs. Firefox, AbiWord vs. OpenOffice, VLC vs. Totem, etc.) makes a much bigger difference.

I did a test a number of months ago that showed the RAM usage of a number of DE's here: [http://www.ubuntuforums.org/showpost.php?p=337695&postcount=4](http://www.ubuntuforums.org/showpost.php?p=337695&postcount=4)

Basically, if you have limited RAM (256 MB or less) it wouldn't matter which DE you use because once you open one application the system is going to start utilizing the SWAP file.  If you've got 512 or more I think your 450 MHz will run quite nicely using any DE.

Hope this helps.
-Dave

---

### Post by IYY on 2006-03-18
I've run it on worse (300 MHz 64 MB). Gnome doesn't like it, but Fluxbox is perfect.

---

