---
title: "ati x800 and blank/black screen"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by racing_snail on 2006-11-26
hello,

I am new to ubuntu/linux, but I am not new to computers (regular user of osx and winxp).

I have been trying to boot up with the ubuntu live cd and I'm having some display issues.

here are some quick specs on my machine:

computer:  shuttle xpc SN95V30
proc:  amd64 3700+
graphics:  ati x800pro
memory:  1 GB ram (2x512mb)
mobo:  nvidia nforce3 
storage:  raid level 1 on two SATA 160GB hard drives (total volume is 160GB because the two drives are mirrored).  using latest nvidia raid driver. 


I have tried to boot up into ubuntu several times.  the first time I tried, I was using the amd64 version of 6.06.  when I tried to boot from the CD, I got the menu screen, and I selected the first option to "boot or install" ubuntu.  I got the splash screen with the progress bar, and then after that finished, the screen went completely blank.  the signal going from the pc to the display was gone and the display said "no signal".  so I restarted and when I got to the menu, I tried boot with safe graphics mode.  I had the exact same problem, the screen went blank.  BUT, the only difference was I heard a musical sound (which was very loud).  I assumed this was a startup sound that plays after ubuntu has booted up.

I couldn't fix this issue, and after reading the forums, it looked like there are known problems with my ati x800 card, I decided to wait until 6.10 came out.  after 6.10 was released, I saw on the forums that people who were having display problems like mine were switching to the "386" version and having better results.  So when 6.10 was released, I downloaded the "386" version of the live cd.  but unfortunately, when I try to boot up with the 6.10 386 CD, I get the same problem, with one small difference.  after I choose "start or install ubuntu" I see the splash screen, and after I see the progress bar finish, the screen goes black.  the video signal is still there, but the screen is black.  the difference is the screen has not gone blank, like what happened before with 6.06/amd64.

If anyone knows what I should do, I would really appreciate the help.  Thank you in advance!

---

### Post by 56phil on 2006-11-26
Hello and welcome. :) My system is nothing like yours, but I experienced the same problem. Why don't you try the alternate install CD? I had success booting from 6.6.01. Good luck.

---

### Post by racing_snail on 2006-11-29
never mind, I did more digging around on the launchpad and ubuntu wiki site. followed directions on this page

[https://wiki.ubuntu.com/EdgyKnownIssues/59618]("https://wiki.ubuntu.com/EdgyKnownIssues/59618")

from there it's just a matter of installing, then upgrading the ati drivers.

---

### Post by TVMA on 2006-12-19
So using the "vesa" driver, does it still allow you to have 3D support, and install beryl / compiz ?  I also have an AMD box with an ATI X800 AGP graphics card. 

Thanks,
Josh

---

### Post by aberry5555 on 2007-01-02
no the vesa drivers won't work at all well trying to muster up 3D, nor will the open source drivers, you should download the proprietary drivers from the ATI website if you wan't to be able to use linux 3D games or Cedega and such. Unfortunately ATI will not let anyone see the source code for the real drivers so you have to go proprietary.

---

