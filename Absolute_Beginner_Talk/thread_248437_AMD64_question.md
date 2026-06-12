---
title: "AMD64 question"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by KGH on 2006-09-01
I running a Athlon64 3200+ Venice. My son is running a 3800+ X2. Neither of us has been able to boot the AMD64 Ubuntu. I have burn several CDs at the lowest speed. The check cd utility says the CD is fine. I've watched the system load & have not noticed any errors. When the OS should start I get a blank screen & nothing else. I see others are having similar problems. Some say the 64 version has some problems other claim they have it up & running. 

Is there problems or is the installation a little more tricky?

I installed the X86 version then switched to the K7 kernel.
KGH

---

### Post by Scorpuk on 2006-09-01
Not sure why you would have a problem, but might sound like something wrong with your video card hence the blank screen.

What hardware do you have?


And I installed the AMD 64 bit version with no problems when 6.06 first hit the download section. Hopefully they have not fiddled with it.

---

### Post by codejunkie on 2006-09-01
> **KGH said:**
> I running a Athlon64 3200+ Venice. My son is running a 3800+ X2. Neither of us has been able to boot the AMD64 Ubuntu. I have burn several CDs at the lowest speed. The check cd utility says the CD is fine. I've watched the system load & have not noticed any errors. When the OS should start I get a blank screen & nothing else. I see others are having similar problems. Some say the 64 version has some problems other claim they have it up & running. 

Is there problems or is the installation a little more tricky?

I installed the X86 version then switched to the K7 kernel.
KGH
you might want to try the alternate or the server install disk's if you havent. they are text based installs but i have had better luck with them doing a server install then i had with the desktop cd. it was very problamatic on my athlon 64 3400+ system, it wouldn't attempt to install unless there 512mb+ memory installed in the system, and both memory slots had to have memory installed even then it was hit or miss. maybe it's just my system but anyway the server server install disk works just fine you just need to run ```
sudo apt-get install ubuntu-desktop
```when you reach the terminal to get a gui, because the server install doesn't come preloaded with one.

---

### Post by xhaan on 2006-09-01
I have similar problems, I can't seem to install 64 bit ANYTHING. LiveCDs won't even boot. I've tried amd64 versions of Ubuntu, Gentoo and FreeBSD, none of them work yet x86 versions all work fine for everything.

I have:
Athlon 3200+
512mb RAM
one 6gig and one 160gig IDE drives
ATI Radeon x1300 pro

Ubuntu x86 installed on the 6gig with absolutely zero problems, installed ATI drivers and now my desktop runs at the highest resolution my monitor can handle.

---

