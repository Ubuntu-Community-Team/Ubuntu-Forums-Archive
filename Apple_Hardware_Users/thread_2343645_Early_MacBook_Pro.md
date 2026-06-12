---
title: "Early MacBook Pro"
date: 2016-11-17
forum: Apple Hardware Users
---

### Post by nul2 on 2016-11-17
Hey Everybody!
I'm completely new to Linux. Yup, I've never used before. I want to learn, but I have an early 2011 MBP 15" with and HD display. I have read that this is an issue with install on Ubuntu. I have my MBP partitioned and ready to go. I have tried to install from USB and when I select install Ubuntu my screen goes black but everything else seems to be working. I hear the bongo drum drop(i think thats the normal sound for Ubuntu, but not sure) and my screen is black as in it is not getting any power. I have tried this multiple time with the same result. I have done some research and supposedly there is a code to punch in that can by pass the radeon HD display, but so far I haven't found one that works. Please help.


Thanks,
nul

---

### Post by howefield on 2016-11-18
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by gsahli on 2016-11-18
Which version of ubuntu and which Mac OS?
I don't have a MBP to experiment with this... Where you would type Live, make it "Live radeon.modeset=-1"

---

### Post by nul2 on 2016-11-19
Mac OS is Sierra version 10.12.1 and from what I know it is GNU GRUB version 2.02~beta2.36ubuntu3...if thats even the information that you want. lol I am that new to Linux. never touched the OS before.Mac OS is Sierra version 10.12.1 and from what I know it is GNU GRUB version 2.02~beta2.36ubuntu3...if thats even the information that you want. lol I am that new to Linux. never touched the OS before.
I went down to install ubuntu in the USB boot drive I made. I hit the e and type that and had the same results. Am i typing code in the wrong place?

---

### Post by g33zr on 2016-11-19
@ nul2: First, you can't install Linux on a Mac with a usb stick unless you format the usb for Mac. See: [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

Second, do you plan to dual-boot or wipe OSX and install Linux? If you plan to dual-boot, I suggest that you install rEFInd on your Mac system and pay close attention to Rod Smith's instructions. See: [http://www.rodsbooks.com/efi-bootloaders/refind.html](http://www.rodsbooks.com/efi-bootloaders/refind.html)

p.s. You'll probably find it easier to burn the ISO onto a DVD and install Linux that way rather than with a usb stick.

---

### Post by nul2 on 2016-11-21
@g33zr, I partitioned my hard drive so that I can use the full linux without wiping my mac partition. I been using a boot USB that I made following this video([https://www.youtube.com/watch?v=IQIaDO9nR6Y&t=9s](https://www.youtube.com/watch?v=IQIaDO9nR6Y&t=9s)) on youtube. I don't know if there is much of a difference between that and the instructions you provided in your link from what I hear my model mac has an ADM video card. I have read they are a pain to deal with. My issue is the turns display off when I select install ubuntu. I hear a bongo drum sound and my display is off as in it is not getting power. I'll have to try your link in when I get back from Thanksgiving. Thanks for the help.

---

