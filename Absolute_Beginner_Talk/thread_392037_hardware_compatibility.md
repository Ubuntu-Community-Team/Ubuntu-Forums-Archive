---
title: "hardware compatibility"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by slampy on 2007-03-24
this is my system, which normally runs windows:

AMD Athlon 64 3500+
Nvidia GeForce 7800 GT video card
2gb of 400mhz ram

I think the main problem is my video card because when I try to install Ubuntu, it will go to that tan colored screen and play the startup music, but when it starts to load the first graphic, it will look all jagged and the image will not completely load, then it freezes.  it does this all the time, I can't get past it to even begin the installation.  Is it possible that I just can't install it on my system?  this has happened with other distros as well.  It will always mess up on some graphical portion of the install and then freeze.  is there anything I can try to get this to work?  thanks.

---

### Post by igknighted on 2007-03-24
Thats odd... that vid card should not have any issues.  Are you sure you don't have a bad burn?  I would install Ubuntu via the alternate install CD (wont cause that graphics card issue) and then boot the first time into recovery mode after install.  You will get a terminal only, so type the following commands:
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```
Then reboot the system and you should be good to go.

---

### Post by slampy on 2007-03-24
where might I get the alternate install cd?  :D

oh, and I forgot to ask before I DLed the last time, but should I DL the x86 version or the 64bit one?  I do have an athlon64 cpu, but I don't use it for 64bit with windows.

---

### Post by igknighted on 2007-03-24
When you chose to downlaod the desktop CD on the ubuntu page, there should have been a choice for alternate as well.  I would stick with 32 bit... 64bit is more work to set stuff up, theres not much performance boost, and some claim it is more buggy.

---

### Post by slampy on 2007-03-24
well here is the DL page ([http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download"))  and I don't see anything that says Alternate.  is it the second option that says  Ubuntu 6.06 LTS - Supported to 2009 ? if not, can you send me a link or tell me exactly where the alternate dl is?  thanks.  after all I'm an absolute beginner.  ;)

---

### Post by lamalex on 2007-03-24
what is your motherboard? did you try booting into safe graphics mode? try adding acpi=off noapic to your boot options (hit f6 before you pick boot live cd  and add those two things). That fixed my problem with graphics on the live cd.

---

### Post by slampy on 2007-03-24
I'll try that, but I did try going into safe graphics mode, and it did the same thing.  I'd still like to know where I can get the alternate install cd.  thanks.

---

### Post by tommcd on 2007-03-24
> **slampy said:**
> I'll try that, but I did try going into safe graphics mode, and it did the same thing.  I'd still like to know where I can get the alternate install cd.  thanks.

Well, they changed the ubuntu.com site all around, so it took me a while to find it too. Go here:
[http://www.ubuntu.com/GetUbuntu/downloadmirrors](http://www.ubuntu.com/GetUbuntu/downloadmirrors)
Choose "other installation options" from a mirror near you.
Then scroll down and find the alternate install CD. Choose PC (Intelx86) alternate install CD.
Be sure to check the md5sums, and burn at a slow speed.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Hope this helps.

---

### Post by slampy on 2007-03-24
I still have to take some time to try getting the install to work, but I just remembered something I forgot to mention before.  Gparted won't even work for me.  it does the same thing where when it trys to begin, there is a black and white screen of just pixels and a black X for the cursor, and it never goes into anything after that.  could my vid card be effecting Gparted as well?

---

### Post by lamalex on 2007-03-24
It's probably not your video card in the first place. What is your motherboard? I have a 7600GT which  works perfectly, its my motherboard that needed some configurationg

---

### Post by Feenix3k on 2007-03-25
I agree it is the motherboard, where in the line of text and boot instrutions do you turn off acip? I put it in but just before it goes to the sweep screen it starts acpi, the blan screen comes up with bglinking  "_" and locks up before the main screen.

---

### Post by Feenix3k on 2007-03-25
> **Iamalex said:**
> what is your motherboard? did you try booting into safe graphics mode? try adding acpi=off noapic to your boot options (hit f6 before you pick boot live cd  and add those two things). That fixed my problem with graphics on the live cd.

I have added acpi=off or noapic, but the apic still loads. Are the 2 commands to be used togather?:confused:

I know my motherboard nFORCE4M-A, AMD Athlon 64 X2, hates linux. But with the Ubuntu live CD 6.06, I can't get it to turn off.

---

### Post by mantawa on 2007-03-25
I have the same problems. 6.10 CD boots to jagged broken ubuntu screen only. I was able to install 5.10 only to have the exact same problem after logon. I tried F6, delete "quiet splash" replace with "break=bottom" only to get: /bin /sh: can't access tty; job control turned off.

I am exreemly green to Linux.

My system:

Asus AN8-E
AMD Opteron 165
Geforce 7800 GT

-Mantawa

---

### Post by Feenix3k on 2007-03-25
I finally got Ubuntu on my desktop. I had to use 6.10 instead of 6.o6. All I did was add acpi=off.

My printer works in 6.06, but trails showed 6.10 it will not.

---

### Post by mantawa on 2007-03-26
That's good to hear, I'll try acpi=off tonight.

---

