---
title: "Problem Installing on Laptop, Please Help"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by 31415271828 on 2007-06-02
I just tried to install the latest version of Ubuntu on my Compaq V6000z laptop.  I am totally new to linux, and so I tried to have it dual booted with XP.  In the installer, I got the graphics to work after I added the VGA=771 parameter.  Otherwise I received just a black screen.  

I installed just fine into a partition that I created.

Then came the time to actually boot off of the hard drive.  The boot process went on, but at some point the screen just turned black, and nothing happened.  :( The fan on the laptop was still going, but the hdd access stopped, and that was the end of that.

What is this problem, and how can I solve this?

Thank you!

---

### Post by AlexenderReez on 2007-06-02
do you sure you have install ubuntu correctly  .........?hm......quite weird either.....do you make swap partition....it is not important.....but sometimes useful........just try reconfigure x-server then......

>  sudo dpkg-reconfigure xserver-xorg

---

### Post by 31415271828 on 2007-06-02
No, I do not have a swap partition.

I am really new to this, but it seemed that the installation completed successfully.  The gui installation finished alright, and at least it got the Ubuntu boot loader installed.

I am wondering if there is some problem with the graphics card?  But then again it is an nVidia integrated 6100...


What is x-serve?

---

### Post by handydan918 on 2007-06-02
Have you tried adding the VGA=771 parameter at boot time? (When the GRUB menu comes up.)
The suggestion to reconfigure the xserver is a good one.
The x-server is the mechanism that supports the GUI. without it, all you have is a terminal (command line) interface.
Not what you want until you are a true guru...

---

### Post by AlexenderReez on 2007-06-02
i'm using nvidia 7900 . . .hm....swap is not important....but it is backup space for Random access memory (RAM) . . ...if you install it in other machine ...just make swap partition about 500 mb...it is more than enough

just reconfigure xserver.....copy my previous command.....then...boot into save mode(second line)

just type those all........

---

### Post by AlexenderReez on 2007-06-02
> **handydan918 said:**
> Have you tried adding the VGA=771 parameter at boot time? (When the GRUB menu comes up.)
The suggestion to reconfigure the xserver is a good one.


hm....i'm not sure either what is its problem....but then reconfigure is just back make auto-detect hardware again....it is not the best choice.....but it may works....i have install several computer using nvidia....never got this kind of problem....even PCI kind of graphic card.....

---

