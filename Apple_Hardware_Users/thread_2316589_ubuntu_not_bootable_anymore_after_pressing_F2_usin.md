---
title: "ubuntu not bootable anymore after pressing F2 using rEFInd on iMac 9,1"
date: 2016-03-09
forum: Apple Hardware Users
---

### Post by Georg_Siller on 2016-03-09
Hi guys!

I'm kind of stuck here, maybe it's part of my recent head injury :( Our small family business needs me so I'll post what I did and how it turned out:

Over a year ago I installed ubuntu studio on an iMac9,1 (2009). I did so using rEFInd 0.9.2 and when I wanted to boot Mac OS X 10.5.8 i just held down the option key on start-up. This displayed ONLY the Macintosh HD and worked perfectly.
Otherwise the machine would go straight to GRUB(2 i guess?!?) and booted ubuntu studio.

I reduced my working hours and started to study at university. So I wanted to set "my" machine back to booting OS X. For the reason that nobody could play around with my beloved ubuntu installation and for the others to use it again as they were used to.
I was in a hurry and read on the rEFInd-Website something about pressing the F2 key before booting. I did so and OS X came up. The problem is, I have no idea how to reach rEFInd, GRUB or anything else than Mac OS X.
I tried out some keyboard shortcuts but nothing seems to help, I don't know how to boot ubuntu again.

I'm grateful for every post, plz help

---

### Post by Bob_Bruce on 2016-03-11
From the terminal run:  sudo update-grub.  After you enter your password it will reset the grub menu. Hopefully on reboot (with alt/option) it will let you choose again. When you do get back into Ubuntu I suggest reinstalling rEFInd from there. 

Enter each of the following lines, one at a time and hit enter, after the first it will ask for your password, then it will prompt you to hit enter, then ask y/n after the 3rd line is entered: 

sudo apt-add-repository ppa:rodsmith/refind
sudo apt-get update
sudo apt-get install refind

Then reboot and you should get the rEFInd menu. To keep people out of your system in the future use a password.

---

