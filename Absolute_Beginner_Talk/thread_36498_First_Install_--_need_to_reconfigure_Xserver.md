---
title: "First Install -- need to reconfigure Xserver?"
date: 2005-05-23
forum: Absolute Beginner Talk
---

### Post by bigbadblo on 2005-05-23
Hey all, just downloaded and installed Ubuntu 5.04 (first time LINUX user)...

However, I ran into some problems during the installation.  I am a Resident Director in a dormitory at a college campus, and have 2 personal computers in my office.  My main computer has Windows XP on it (which I'm very comfortable with), while the second computer acts as our FileServer (and occasionally a BF1942 server)...

So I did my reading, used PartitionMagic and setup the FileServer in such a way that I could dual-boot WindowsXP and Ubuntu using GRUB.  But here is where the problems started:  the installation would error out at random points.  After trial and error, I resolved that the issue was some bad memory in the FileServer, which was corrupting the installation.

So I pulled the main hdd out of the FileServer, and brought it over to my main personal computer, where I was able to install Ubuntu no problems -- even loaded it up and ran around inside of it for awhile.  After playing with it for a bit, I decided to swap the hdd back to the FileServer and get that machine back up and running.

Everything seemed to be working well until, during the boot procedure I received an error stating that the X Server could not be started due to it not being setup correctly... it also states that the X Server will be disabled, and that I should restart GDM when it is configured correctly.  I assume I'm experiencing this due to the fact that the system files were initially setup to run my Nvidia FX5900 on my personal system (where I installed Ubuntu) versus on the FileServer where I have an old Radeon 7200.

So what should I do?  I've snooped around the net a bit, crawled through different forums, etc.  But part of my problem is that I don't understand Linux-speak yet, and so most of the solutions are all french to me...

I'd appreciate any help or pointers anyone can give me!

Thanks so much,

bigbadblo

---

### Post by jkndrkn on 2005-05-23
I've run into posts relating to your problem. It seems that the ubuntu iso file is _very_ sensitive to errors during burning, and that most of these errors arise in problems with the xserver.

Try burning your iso with all possible error correction and a very slow burning speed. Then try reinstalling.

Hope this helps.

---

### Post by dekoi on 2005-05-23
First, welcome to the community! I hope you enjoy your stay, and stay.

It doesn't sound like you've put a lot of important data on the Ubuntu partition, and the simplest solution would probably be to replace the bad memory in the fileserver, then reinstall Ubuntu on the fileserver--where it's going to be used. 

You can reuse the partition you made for Ubuntu.

Also, have any periphery (printers, scanners, whathaveyou) on your fileserver up and running when you re-install Ubuntu, unlike Windows, it will configure everything as it installs.

Hope that helps you out.

---

### Post by bigbadblo on 2005-05-23
Hmm...

Just to clarify -- the installation is working (so long as the hdd with Ubuntu is in the system it originally installed upon).

My concern is growing from the fact that when I took the hdd with Ubuntu and replaced it in its original environment, that Ubuntu had installed drivers for my video card based upon what it had originally seen (GeForce FX5900) compared to what it is currently working with (ATI Radeon 7200).

Is it an installation error?  If i bring the hdd back to my personal computer and install it as the master drive, Ubuntu loads up right as rain.  If its in the FileServer as the master drive, I am left with errors loading GDM.

I'd reinstall in the FileServer -- but I have an inclination that it won't succeed...

Any other thoughts?  (PS... i actually thought the burning of the .iso was my initial problem -- I switched over to the good Sony CDR media and burned at 1x using burnatonce.)

thx,

bigbadblo

---

### Post by bigbadblo on 2005-05-23
Yea...

The memory might just have to go.  Its weird though, i just installed Windows XP on that system yesterday and I didn't have any problems.  Usually bad sticks will corrupt an XP install as well... funny that only Ubuntu caught it.

I'm sure they're bad thou... looks like it'll be a few more days until I get this dual boot working!

Thanks for the help thou,

blo

---

### Post by Mez on 2005-05-23
Hi there.

Assuming you havent manually changed any of your configuration files for X manually, then you should be able to run the following command in a shell

sudo dpkg-reconfigure xserver-xorg

and that should run you through setting up X again (make sure you have your monitor and video card detaisl to hand - you'll need to know (specially type and manufactrer of your card, and vertical and horizontal sync rates of your monitor)

Other than that, it should be pretty simple. It's not that hard to reconfigure.

---

### Post by bigbadblo on 2005-05-23
Mez --

Beautiful.  Followed your command prompts, and it couldn't have been easier!  Thanks for taking the time to help me out!

blo

---

### Post by aussieskin on 2005-07-06
Hi all I also have the same problem....although I so dont want to reinstall ubunutu!

I was trying to get sound working, and followed some instructions from a thread here, then when I rebooted I got the same error

"I cannot start the x server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?

I say yes and it all means nothing, but then it gives me the option to reconfigure and I do but it aint working!

I am sure I am putting everything right

---

### Post by Elim on 2006-07-05
I am having the same problem that aussieskin is.  I upgraded to Dapper with no problems, and everything seemed to boot correctly, but when I got to the graphical login, instead of loading gdm it came up with a blank screen for a moment, then the error message that aussieskin quoted.

At that point my keyboard is non-functional, so I can't acutally read the X server output.  My only recourse was to turn off the comp via the power button.

For reference: Intel 815 chipset, 500 Mhz, 512 MB of PC133 SDRAM, no video card.

Thanks for your time. :)

---

