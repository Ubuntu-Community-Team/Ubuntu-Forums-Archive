---
title: "Information needed before video driver install"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by Aramis on 2006-04-14
Hi y'all,

I managed to install Ubuntu on my old Laptop using various NetBoot/NetInstall tutorial. Although, I was not expecting flashing performance and graphics I must admit that the overall feel of using Ubuntu is "slowliness". Thus, I am very keen to upgrade my video driver in order to see if that makes things better.

Of course, I did search the forum and landed on the thread authored by ArnieBoy. I think I am the target audiance, my Laptop SAMSUNG A10 has a built in S3 Savage Hotkey graphic card. However, I am not keen on executing all these commands blindly, or at least without understanding what I am doing. What if my distro is already properly configured, and maybe what I have is as good as it gets? In order to answer this question I believe I must gather information on my current systen.

1 - ArnieBoy suggests that the Kernel should be changed/altered. How do I find the Kernel version that I am currently using?
2 - ArnieBoy mentions old AMD/Intel chip. What is he refering to? CPU or GPU? if he is refering to CPU how does one know about the age of the CPU? My laptop has a Duron Processor, does that fall into the "old" category?
3 - How do I make sure that my Video Card is not fully recognised yet? I see that there is a device manager in Ubuntu. My card is listed, few items have values but I cannot conclude a thing from it.

Cheers,

Ar@mi$

---

### Post by cilynx on 2006-04-14
Welcome to the fold:

1 - 'cat /proc/version'
2 - CPU, 'cat /proc/cpuinfo', you already know it's a Duron.  That's not that old.
3 - I've never found the 'device manager' useful...

Now that I've answered your questions, I'm going to ask some of my own...

What is "slow" about the system?  In my experience, unless you're trying to do neat 3D stuff, your graphics setup is never the reason that the system is slow.  How much RAM do you have in the system?  If you look at /var/log/Xorg.0.log, does it talk about your S3 or does it say that it fell back to the VESA driver?  In /etc/X11/xorg.conf, what driver is mentioned for the graphics card?  Are you trying to do neat 3D stuff or just get a functional display?

Good Luck

Edit: fixed location of xorg.conf

---

### Post by Aramis on 2006-04-14
Good Lord I could not find the thread... good thing I bookmarked it :mrgreen: 
Well, then...

1 - 
```

Linux version 2.6.12-10-k7 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11 16:59:38 UTC 2006

```
2 - 
```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 7
model name      : mobile AMD Duron(tm)
stepping        : 1
cpu MHz         : 500.155
cache size      : 64 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 990.21

```
3 - was that a Digd at the dev team :p 

Your question answered.

I found it slow because:
menus and so on appear in a choppy fashion . It feels exactly as in Windows with the default drivers hence my primary observation.
videos in MPlayer do not play well. I installed this application and some codes (non commercial ones) via Automatix.
Ah the RAM, that might just be it. I have 256 MB from which  32 MB are shared with the video card.

According the Xorg Log the card is recognised alright:
```

Device "S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)"

```

I do not have a file named xorg.conf in etc. When I do "vi /etc/xorg.conf" it says it is a new file :neutral: 

No I have not trying to get fancy 3D and so on, just something "usable". Although, I installed Ubuntu for research purposes (e.g. writing / testing app in C# with Mono) this move was also motivated by the advise of friends who argue Linux is a good way to recycle old hardware. On this matter I must agree. At work we use FreeBSD 5.4 on PIII 700 with 128 MB of RAM for our networks experiment and it works well (ok ain t no GUI on them :???: ). My Laptop could not longer cope with WinXP...

Finally, **cilynx** do you think my video card is up to date? If not, is it a waste of time to update/upgrade.....

Thanks a lot for you help :mrgreen: 

Ar@mi$

---

### Post by cilynx on 2006-04-14
I'm going to attack your last question first:

Is your card up to date?  Well, that depends on what you want it to do.  My personal, non-professional suggestion is to go out and get yourself an nVidia something or other.  At least a 5200.  I run dead smooth, with 3D crap on a 5200.  That should set you back well under $100.  I've never had the greatest luck with S3 under Linux.  However, S3 is officially reasonably supported, so if you want to fight with it, you're bound to learn something useful.

I pointed you to the wrong location for the xorg.conf file.  It's in /etc/X11, not /etc/.  Sorry about that.

To the best of my knowledge, the driver you should be using is 'Savage'.

Let me know what you find...

Also, for older machines without much RAM / graphics hardware, look into [UbuntuLite]("http://www.ubuntulite.org") and/or [Xubuntu]("https://wiki.ubuntu.com/Xubuntu").  Both are designed to look good and run well on older hardware.

---

### Post by Aramis on 2006-04-15
Hello again **cilynx**,

At the moment I run Ubuntu on my old laptop, it is not that I am skint but going out to buy a new video card isn't going to help ;) As I pointed out in a previous message if this is the best I can get I ll live with it. As always it is a matter of having the "proper" information. This probably stems from my life as a research student :-k 

I did "vi /etc/X11/xorg.onf" and effectively the driver states "savage". Unfortunately, I could not find the version number of this driver. However, chances are that it is "newer" than the driver package I go off the XFree, or something like it, that said it is the driver 4.0.3 (there is an "O" file in it).

Finally, thanks for the link to the various Lighter version of Ubuntu. I learned the hard way the issues linked to having a "more beautifull" desktop with KUbuntu. I wanted that in the first place and it back fired when I wanted to develop in C# using MonoDevelop.... Therefore, for the time being I am going to stick with Ubuntu (research comes first :mrgreen: ).

In the thread "is Ubuntu for you" the author said there was a steep learning curve... Well he ain t kidding ;) 

Ar@mi$

[edit] I would buy more RAM for my laptop though :mrgreen: [/edit]

---

### Post by cilynx on 2006-04-15
Many people say there's a steep learning curve now.  I don't think it's much of anything compared to what it used to be.  According to your sig, you've been working at Linux for a couple of days, and you're to the point of trying to get your GUI working the way you want it.  Congratulations.

When I first installed Linux (Slackware 3, from 3.5 floppies), It took me a month just to have basic hardware support.  Keep in mind, this was back when compiling your own kernel wasn't just a learning experience, it was pretty much manditory...and it took about 20 hours for my 386 SX/25 to get through it.  Nothing like getting up in the morning to realize you forgot to build in some driver and you have to start the compile all over.

I'm not trying to brag or make myself look experienced here.  God know, most folk around here know more than I do.  I'm just trying to point out how far the Linux world has come in usability for the common man.  It's a good day when users can hop on a forum and troubleshoot their GUI.

---

### Post by Aramis on 2006-04-15
Well, thanks for the insight **cilynx** ! Scary flash back though :neutral: 

I am going to keep the drivers the way they are now. Maybe some time soon I'll know enough to make things soomther on my laptop.

Anyways, my questions are answered :mrgreen:

Ar@mi$

---

