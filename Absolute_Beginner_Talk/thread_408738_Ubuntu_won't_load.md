---
title: "Ubuntu won't load"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by kayos82 on 2007-04-13
Hi,

I am a Windows user by trade and am trying to experience some linux. I used Redhat long, long ago when I was in college so I know a little bit about it but not as much as I know I should.

Anyway, here's the deal:

I am trying to make a dual boot system of my Dell Inspiron 600m (XP/Ubuntu). However, every time I try to load Ubuntu using live cd I get a "CRC Error --System Halted". Now I have done a bunch of research and tried re-downloading and re-burning. I also tried burning it at the slowest burn rate possible as well as doing both the cd check and mem test. I get nothing from any of it! Only this stupid "CRC Error".

I really want to try this flavor of linux, but it just doesn't look like it is going to happen for me.

*sigh*

Please help me :confused:

---

### Post by xopher on 2007-04-13
This error implies corruption in some files, either the image is corrupted, or then there's something else causing the corruption on-the-fly. If you've verified the md5checksums of the iso, tried another burner (maybe at a friend), then it's starting to lean towards a hardware problem.. Maybe a BIOS setting, maybe something else.

---

### Post by kayos82 on 2007-04-13
> **xopher said:**
> This error implies corruption in some files, either the image is corrupted, or then there's something else causing the corruption on-the-fly. If you've verified the md5checksums of the iso, tried another burner (maybe at a friend), then it's starting to lean towards a hardware problem.. Maybe a BIOS setting, maybe something else.
Now, the disc I'm using worked just fine on a friends HP laptop. I did read some other things about it being a BIOS setting. If it is the BIOS then I wouldn't even know where to begin to look in there... Got any pointers to push me in the right direction?

---

### Post by HereInOz on 2007-04-13
This may sound odd, but I recently had problems installing Dapper on an old IBM thing, and kept getting corrupted file reports and all that stuff, and I swapped out the CD drive and replaced it with one that was coincidentally set as secondary master, rather than slave, and the install ran perfectly.

I then got curious and re-set the original drive to master, and re-ran the installation, and everything went OK.  I know that this should not make a difference, and on other machines it doesn't, but I just throw this in as a remote possibility.

---

### Post by kayos82 on 2007-04-13
> **HereInOz said:**
> This may sound odd, but I recently had problems installing Dapper on an old IBM thing, and kept getting corrupted file reports and all that stuff, and I swapped out the CD drive and replaced it with one that was coincidentally set as secondary master, rather than slave, and the install ran perfectly.

I then got curious and re-set the original drive to master, and re-ran the installation, and everything went OK.  I know that this should not make a difference, and on other machines it doesn't, but I just throw this in as a remote possibility.
Ok, I tried the CD in my desktop and it works just fine in live cd mode. I can't even get live cd mode without the CRC Error on the laptop. Now I can't swap CD drives on my laptop (which is the machine I'm trying to install on). I would really like to see some suggestions about what I can do in the BIOS to make loading this OS possible.

---

### Post by kayos82 on 2007-04-13
No more ideas?

---

### Post by kayos82 on 2007-04-14
I really need help with this.

---

### Post by chalex on 2007-04-14
It sounds like a hardware problem to me.  You said the disk works fine in other machines, so the variable is your laptop.

Try burning and running a memtest86 cd: [http://www.memtest.org/](http://www.memtest.org/)

Try running your manufacturer's hard disk diagnostics.

See if your laptop has a built-in diagnostic routine.  Since you have a Dell, it should say something like "press F10 to access the diagnostic partition"

---

### Post by kayos82 on 2007-04-14
Ok, I've run memtest and figured out it was a good cd and all that. I have tried configuring a bunch of BIOS settings to no avail...

This is frustrating as crap. I have never had this much trouble getting an OS onto a machine before. I know it is the machine, I'm just trying to figure out what about the machine. It is kinda hard when the only thing I get from it is this and ONLY this:

crc error

    --System Halted

BTW: I tried booting another version of linux from live cd and got nothing but a blank screen. I absolutely know it is the laptop doing it, I just need some pointers on what could be causing this mess.

- thanx for all the previous attempts to help me! Got any other ideas?

---

### Post by rajeev1204 on 2007-04-14
dont rely too much on memtest even though it is preferred tool

try replacing the ram modules so u can be sure


this happened to me also

---

### Post by kayos82 on 2007-04-15
I guess that is my last option... :(

---

### Post by kayos82 on 2007-04-15
Ok, well I've tried many tests on my linux venture and found that no live cd distro will boot on this laptop. I also tried booting live cd on a friends laptop and it didn't work then... I then tried on my brother's laptop and viola it works!

The difference being that my friend and I's laptop is a Pentium M processor, and my brother's is an AMD.

I have been doing some research on the Pentium M chipset w/ centrino to no avail so far... Anybody have any ideas? I was thinking I could do something in the boot options, but I'm not sure.

---

### Post by kayos82 on 2007-04-16
no ideas?

---

### Post by Radiera on 2007-04-27
The fact is that this is a problem totally ignored by ubuntu. A huge problem! Windows works, debian works, ubuntu doesn't. If i see any more brght ideas like 'try changing your ram' I'm going to throw up.

THIS KIND OF PROBLEMS IS THE REASON WHY DEBIAN TEST THEIR PACKAGES FOR SO MUCH TIME! PEOPLE, LEVE THIS UBUNTU IDIOCY AND GO FOR THE REAL THING!

---

### Post by solarix on 2007-04-27
> **Radiera said:**
> The fact is that this is a problem totally ignored by ubuntu. A huge problem! Windows works, debian works, ubuntu doesn't. If i see any more brght ideas like 'try changing your ram' I'm going to throw up.

THIS KIND OF PROBLEMS IS THE REASON WHY DEBIAN TEST THEIR PACKAGES FOR SO MUCH TIME! PEOPLE, LEVE THIS UBUNTU IDIOCY AND GO FOR THE REAL THING!

Please stop screaming.

I personally use Free BSD, Open BSD, Debian, Solaris and Ubuntu.

The Ubuntu Packages are well, if you use Debian Testing or unstable you could ran into same Problems.

Nothing is perfect, and believe m Debian is not more stable or better tested, than Free BSD Packages, or Solaris Packages. 

It´s no question that i read in the last few weeks something about CRC Errors, not only in this Thread.

But I´m using Ubuntu on my Thinkpad A 31 since two years. At the last weekend i made a complete new Install with  the Alternate CD and it wasn´t a Problem. I have to say that i never use the Standard CD, i always use the Alternate CD cause i have more influence on the whole process of installing.

---

