---
title: "[SOLVED] Help installing"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Stache on 2008-02-17
New to Linux and Forums, please excuse any gaffs.

Read the installation information and followed it to INSTALLATION, then I get a black screen with:
.
.
.
Starting kernal event manager...  [OK]
Loading Hardware drivers...

This is where the curser goes to the far right, stops blinking and the CD stops.

I have a HP Laptop dv6000 with AMD dual core 64 on an HP xB3000 expansion base.  A wireless hook-up through a DLink router.

Any help will be appreciated.  It is late here and I will sign off in about 5minutes.  Check back tomorrow.
Stache :-})

---

### Post by bodhi.zazen on 2008-02-18
Hard to say for sure.

First, make sure the downloaded iso and CD are OK

Check the MD5SUM :

	Windows : [http://penguinbyte.com/software/md5filecheck/](http://penguinbyte.com/software/md5filecheck/)

OK, the other potential problem is with your videocard, do you know your video card ?

---

### Post by wolfen69 on 2008-02-18
you might want to visit this thread for HP laptops [http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220) 
your laptop is not known to be the most linux friendly.

---

### Post by Stache on 2008-02-18
Bodhi,
PS-Video Card is NVIDIA GeForce Go 7200. Generic PNP Monitor.
Stache

---

### Post by nsimeone2000 on 2008-02-18
I hope you are using the Alternate CD (because live don't work for Nvidia/AMD combos), and I would only put on 7.04, I had lots of issues installing Ubuntu, and I have an HP DV9000 series....with the AMD/Nvidia combo.

Another thing that helped me is when I had the alt-cd in there, press f6 and type "noapic " (notice the space after noapic/) then install.  Worked like a charm after that and I didn't have to go into Grub.

---

### Post by Stache on 2008-02-18
Nsimone
I have 7.04 but had problems with it also.  This was about six months ago and I do not  remember the specifics.  I will try it again considering all the problems with 7.10.  Also, which is the alternate CD vs Live CD?  BTW this is a dual boot with Vista Home Premium.

---

### Post by smartboyathome on 2008-02-18
Use 7.10. I have an AMD Athlon 64 and an NVidia 6100, and it booted fine. I would go with the alternate install of 7.10, though, and install the drivers for it after.

---

### Post by Stache on 2008-02-18
O. K. Ubuntu Community Helpers,
Here is where I am now.  I installed 7.04 and everything seemed to go fine till the boot-up.  At the splash screen, I get UBUNTU then below that 10 small vertical lines (Progress bar??).  It only gets to one+bars and hangs. the only way out is power swithch shut-off.
stache:-}(

Out of town till next week 2/24
Thanks

---

### Post by nsimeone2000 on 2008-02-20
Did you get the alternate CD?  The alternate CD is the one that is in Text Mode.
Here is a link: [http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)
The Live CD is the one that installs without text mode. 

Basically scroll down to the bottom, where it says alternate go ahead and download that one, you can do 64 bit if your computer supports it (I am running 64 bit)

Before you hit enter once you get the text mode cd put in, press f6 and type in noapic

Then run the text mode install, after it installs, the computer will restart, it should boot up just fine and dandy.

send me a PM if you need some help, I get lost in these forums, sorry about the delay in writing you back.

---

### Post by Stache on 2008-03-02
After some iterations, everything went well.  I used the tutorial on this forum.

I am still learning Ubuntu and working with Windows (this post).  The most difficult was getting the partitions right.  I used the alternate CD and at the splash screen after pressing F6 i typed "noapic".

It took me some time to get to the TERMINAL (NOTE, if you use a left handed mouse change it first so you can get to TERMINAL) and figure out the Grub.  Also, after start-up there were 189 updates.  After the updates, in the Grub I had two versions a -15 and a -16.  I commented out the lines for the -15 and all seems to work fine.  Set-up of the internet connection worked well also.  I used the information that was supplied by my IPC on my initial installation in Windows.  There was some translation of terms but it did not take much to guess what was needed.

Thanks to those who helped and to the information on the forum and website.

Stache

---

