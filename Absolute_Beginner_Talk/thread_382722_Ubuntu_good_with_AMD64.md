---
title: "Ubuntu good with AMD64???"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by luckylucky on 2007-03-12
Hi,

I am contemplating building a computer from scratch and want dual core power.  I am thinking about using an AMD 64 chip (below is specs of chip) and am wondering if the Ubuntu distro for AMD64 chips works well, identical to the regular Ubuntu, or if there is some differences some how.  Any feedback on the AMD64 version of Ubuntu would be appreciated.

Thank you in advance!
LuckyLucky


AMD Athlon 64 X2 5200+ Dual Core Socket AM2 2.6GHZ chip

---

### Post by Songwind on 2007-03-12
The distro works great.  However, there are issues with software availability.  Simply put, there are a lot more software options at 32 bit at this time.  Many of them will work fine under the 64-bit version anyway, but it takes more finagling.

Running the 32 bit version on the AMD64 is also a perfectly valid option.  Recent benchmark tests suggest that there's not a large amount of performance to be gained with the 64 bit version just yet.

---

### Post by thelinuxguy on 2007-03-12
I have an AMD 3600+ Dual Core with ASUS M2NPV-MX and have had no problems, whatsoever, this far. I am running the 32 bit version of Edgy because of software issues with the 64 bit version. Not that this software compatibility problem is with Ubuntu only. It holds good for WinXP and maybe for others as well.

So while dual core power is a good idea....installing the 64 bit version may not be. I would suggest stick to the 32 bit version for some more time.

---

### Post by Spike-X on 2007-03-12
I'm running the AMD_64 version of Edgy. The only major issues I've had have been installing Flash Player (managed to get this done using ndiswrapper) and ntfs-config, which I only needed so I could give write permission to my external HD.

---

### Post by Songwind on 2007-03-12
One of my biggies was printer support.  There are no 64-bit drivers for my printer and CUPS at 64-bits won't use a 32-bit driver.  It was a chore.

I had to reinstall anyway so I decided to try out the 32 bit version.  I found that Firefox is more stable now, too, more's the pity.

---

### Post by luckylucky on 2007-03-13
First of all, thanks for everyone's help... really appreciated.

[COLOR="Red"]QUESTION[/COLOR]

Are you saying that you can install the regular plain default Ubuntu install in a system using AMD64 chips?  I thought, from what was said on the home page of Ubuntu, that if you have AMD64 that you need to use the special 64bit Ubuntu install.  Will the plain Ubuntu install work perfectly in a 64bit AMD computer?  If so then why do they tell you to install the alternate version?

Thanks in advance for your answers

---

### Post by 67GTA on 2007-03-13
Installed edubuntu on amd athlon 64 3800+. Only problem is the mouse freezes every few minutes. Probably bios setting though.

---

### Post by Songwind on 2007-03-13
> **luckylucky said:**
> First of all, thanks for everyone's help... really appreciated.

[COLOR="Red"]QUESTION[/COLOR]

Are you saying that you can install the regular plain default Ubuntu install in a system using AMD64 chips?  I thought, from what was said on the home page of Ubuntu, that if you have AMD64 that you need to use the special 64bit Ubuntu install.  Will the plain Ubuntu install work perfectly in a 64bit AMD computer?  If so then why do they tell you to install the alternate version?

Thanks in advance for your answers

Oh yeah, absolutely.  I am having 0 problems with it.  At least, no problems due to the 32 bit OS.  Composite graphics support is spotty and sometimes makes my apps die, but since I accepted that fact of life and turned it off it is very smooth.

I don't remember seeing it say that you *needed* the 64-bit version when I downloaded.  Where did you see that?

---

### Post by igknighted on 2007-03-13
> **luckylucky said:**
> First of all, thanks for everyone's help... really appreciated.

[COLOR="Red"]QUESTION[/COLOR]

Are you saying that you can install the regular plain default Ubuntu install in a system using AMD64 chips?  I thought, from what was said on the home page of Ubuntu, that if you have AMD64 that you need to use the special 64bit Ubuntu install.  Will the plain Ubuntu install work perfectly in a 64bit AMD computer?  If so then why do they tell you to install the alternate version?

Thanks in advance for your answers

:) of course.  x86_64 architecture is a subset of x86.  This means it is fully compatible with x86.  It's like the square/rectangle arguement.  A square is a rectangle, but a rectangle is not a square.  AMD64 chips are x86 chips, but standard x86 chips are not AMD64 capable.  Note: Intel chips such as Pentium D and C2D are "AMD64" capable as well.

---

### Post by luckylucky on 2007-03-13
SongWind,

I must have been hallucinating.  Looking back at the home page it does mention that there is a version for AMD64 so I guess my brain jumped to the conclusion that you must use it if you have 64bit chips... but nowhere does it say that you must.  I'm going to visit a local computer retailer (BestBuy) with the plain 32bit live CD of Ubuntu in hand to testdrive it on some AMD64 machines.

[COLOR="Red"]QUESTION[/COLOR]

You mentioned that something didn't work & you had to disable it.  Is that because of your AMD64, or just because that thingy was flaky?  

[COLOR="Red"]QUESTION 2[/COLOR]

**Bottom line... is there *ANY* disadvantage to using an AMD64 chip whatsoever, and would I be better off sticking to an Intel (dual core) 32 bit chip, or does it not really matter at all?**

[COLOR="Red"]EVERYONE[/COLOR]

Thanks everyone for such a speedy reply - I am still in awe of how awesome this forum community is!

---

### Post by thelinuxguy on 2007-03-15
> **luckylucky said:**
> 
**Bottom line... is there *ANY* disadvantage to using an AMD64 chip whatsoever, and would I be better off sticking to an Intel (dual core) 32 bit chip, or does it not really matter at all?**


By my experience with AMD64, there is NO disadvantage in using an AMD64 chip. I haven't come across any problems whatsoever.

---

### Post by luckylucky on 2007-03-16
Thank you everyone for your help on this matter, I am very appreciative to everyone's input.  I'll be seriously thinking about the specs for the new system soon, and it'll probably be a dual AMD64. 

Ubuntu Rocks! :guitar:

---

