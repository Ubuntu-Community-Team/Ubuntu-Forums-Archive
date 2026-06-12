---
title: "installation problems"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Joe R on 2008-01-15
I have downloaded the CD. Wiped windows XP off. put CD in and clicked install Ubuntu. it then churns away before presenting me with a milky silvery screen. Another thread asked someone the question "Does ctrl alt F1 get to the address line". Yes it does so I have a compatability issue with the graphics card support. 

What can I do?

---

### Post by dstew on 2008-01-15
I assume you are using a LiveCD, and clicked "Start or Install Ubuntu" from the first menu, then got the milky screen. Is this correct?

---

### Post by Joe R on 2008-01-15
> **dstew said:**
> I assume you are using a LiveCD, and clicked "Start or Install Ubuntu" from the first menu, then got the milky screen. Is this correct?


Yes

---

### Post by Law506 on 2008-01-15
What kind of video card? onboard video, nvidia, ati, etc?

---

### Post by zz_tops on 2008-01-15
did you try boot up in "safe mode"

---

### Post by Joe R on 2008-01-15
> **Law506 said:**
> What kind of video card? onboard video, nvidia, ati, etc?

The computer is a emachine c633 with 10 gig hard drive. the graphics card is the one on the motherboard. I have taken a hercules3d prophet out of the machine when i formatted the hard drive.

The mouse does work. When I get the milky screen there is a pointer which I can move.

---

### Post by Joe R on 2008-01-15
> **zz_tops said:**
> did you try boot up in "safe mode"

I know I can start a windows system in safe mode but windows has been taken off.

Do you think reinstalling a version of windows may help the ubuntu installation then remove windows later?

---

### Post by dstew on 2008-01-15
It looks like your LiveCD is not working with your hardware. You could try kernel parameters, but if you know you want to install, use the Alternate Install CD. It installs the same Ubuntu system using a text-based interface that avoids graphics difficulties. You get is from the same Ubuntu Download page, just click the box beneath the Start Download button.

---

### Post by Joe R on 2008-01-15
> **dstew said:**
> It looks like your LiveCD is not working with your hardware. You could try kernel parameters, but if you know you want to install, use the Alternate Install CD. It installs the same Ubuntu system using a text-based interface that avoids graphics difficulties. You get is from the same Ubuntu Download page, just click the box beneath the Start Download button.

Thanks

Ill start on that straight away

---

### Post by Law506 on 2008-01-15
> **Joe R said:**
> I know I can start a windows system in safe mode but windows has been taken off.

Do you think reinstalling a version of windows may help the Ubuntu installation then remove windows later?

I think what he meant was booting up in safe mode from the live cd.  installing windows again shouldn't have any effect on the Linux side i believe.

Also, there are other brands of Ubuntu, if you got the time, maybe you could try Xubuntu or even GeUbuntu, both are good for older systems and non so top of the line ones.

---

### Post by Joe R on 2008-01-15
I have downloaded the alternative Cd. I got the same screen as before but I pressed ctrl alt F1 and pwd then ls. I got a list of items in dark blue writting "Desktop Documents Music Pictures Public Template and Videos" 

I put the line of code sudo dpkg etc but nothing happened.

A bit more positive as it showed the list and the command line was working.

---

### Post by Joe R on 2008-01-15
> **Law506 said:**
> I think what he meant was booting up in safe mode from the live cd.  installing windows again shouldn't have any effect on the Linux side i believe.

Also, there are other brands of Ubuntu, if you got the time, maybe you could try Xubuntu or even GeUbuntu, both are good for older systems and non so top of the line ones.

There is a graphics safe mode which I had tried as well as the OEM type of install.

I am glad I dont have to install windows again as this would defeat the purpose of this project.

I like the sound of using Xubuntu.

The alternative CD of ubuntu has gone a little further on the installation so I shall persevere for another day.

---

### Post by dstew on 2008-01-15
Did you complete the installation process using the Alternate Install CD? It sounds like you did. The **ls** command lists directory contents, and the contents sound like typical home directory folders.

If you entered **sudo dpkg-reconfigure xserver-xorg** on the command line something should have happened. Did you get an error message?

---

### Post by Joe R on 2008-01-16
> **dstew said:**
> Did you complete the installation process using the Alternate Install CD? It sounds like you did. The **ls** command lists directory contents, and the contents sound like typical home directory folders.

If you entered **sudo dpkg-reconfigure xserver-xorg** on the command line something should have happened. Did you get an error message?

I didnt get any message on Ubuntu but I did with Xubuntu.

The errors shown are
Buffer I\o error on device SRO logical block 277978
Squashfoerror Sb_bread failed reading block 0x87585
Squashfoerror unable to read cache block 21d60aec:dd1
Squashfoerrorunable to read inode
Squashfoerror sb_breadfailed reading block 0x87585
Squashfoerror unable to read cacheblock 21d60aec:d61
Squashfoerror unable to read inode

Thanks
Joe

---

