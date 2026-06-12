---
title: "dual boot windows/ubuntu problem"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by hibajugala on 2008-01-04
ok, well i have had windows xp on my main hard drive (hda1) and ubuntu 7.10 running off of my external harddrive (hda2)

the problem is that my pc wont boot into windows if my external hardrive is not plugged into my pc, then I get "error 17" in the grub menu and my computer wont boot at all.

I have tried using Gparted to remove the /boot flag from my external and formatting it and it still wont boot to windows.

right now all I want is to be able to use my external as something other than a boot drive, and to be able to run windows by itself. I do want to get rid of ubuntu for now, but I will probably install it later without making this mistake

---

### Post by PPAAUULL on 2008-01-04
I think that happens because the MBR needs that drive there. you should have put GRUB somewhere else to use Linux on the external.

---

### Post by chrome007 on 2008-01-04
Hello,

I agree with "hibajugala"  that early in the installation process I should have the option to not install a boot loader but instead have the option to boot into Ubuntu through a floppy disk.  

I have the exact same proolem when I loaded on Ubuntu and in the install it never gave me an option to not install a boot loader but instead use a floppy to boot.

This is one of the most basic functions that you cannot ignore or make difficult to find in the installation process.

So, my question remains as to how do I install Ubuntu so that it will not touch my Windows partition, and how do I create a boot disk that will boot Ubuntu.  I hope this will be a simple process because it shoul be.

Chrome

---

### Post by ubutufan on 2008-01-04
Your windows MBR (Master Boot Record is destroyed. 
Use the XP installation disk and go for R (repair). Then type fixboot. Also have a look at [http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20Repair%20the%20Boot%20Sector:](http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20Repair%20the%20Boot%20Sector:)

---

### Post by ubutufan on 2008-01-04
> **chrome007 said:**
> Hello,

I agree with "hibajugala"  that early in the installation process I should have the option to not install a boot loader but instead have the option to boot into Ubuntu through a floppy disk.  

I have the exact same proolem when I loaded on Ubuntu and in the install it never gave me an option to not install a boot loader but instead use a floppy to boot.

This is one of the most basic functions that you cannot ignore or make difficult to find in the installation process.

So, my question remains as to how do I install Ubuntu so that it will not touch my Windows partition, and how do I create a boot disk that will boot Ubuntu.  I hope this will be a simple process because it shoul be.

Chrome

You have an option. It is in the final stage of installation. Right side down it says Advanced. Pressing this will allow you to define what partition you want to install GRUB

---

### Post by ubutufan on 2008-01-04
and if you need a-z instructions, you may follow this link
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

It is a fantastic guide and it DOES NOT change your windows installation. Just make sure you READ IT from start to end

---

### Post by chrome007 on 2008-01-04
Hello,

You guys are the best.  I will look into everything you have provided.  However, I have another question.  If I select "Advnaced" option and place the boot loader on another parition will it take the default booting order over from Windows?  In other words will it allow my Window boot manager to stay intact or will it destroy it?

Thanks,
Chrome

---

### Post by ubutufan on 2008-01-04
As I said before read Matthew Miller instructions.

As an example. If you had XP installed prior to any other operating system, then the MBR would be on partition /dev/sda0 (assuming you have a sata disk installed). If you install GRUB on /dev/sda5 (example) then the XP MBR is unharmed.

But again read the instructions. It is all in black and white

---

### Post by jonny5tails on 2008-01-04
Dear hibajugala,
  What EXACTLY did you do with Gparted?

---

### Post by esteckis on 2008-01-04
I am still a linux newbie, but could he not try the startup manager so he can set windows as default loader and have the choice to run UBUNTU when he has the usb drive plugged in?

---

### Post by meindian523 on 2008-01-04
That's possible if Grub is installed to the MBR of the internal HDD,thence when the external is plugged in,it will enable to boot to Ubuntu and when it's not plugged in,you can boot Windows and when the external is not plugged in and you try to select Ubuntu,grub will show Error 18(15?I forget) that is File Not Found.

---

### Post by hibajugala on 2008-01-12
THANKS! fixing the MBR with the FIXMBR command when I put in the windows installation disks worked perfectly fine! :)

---

