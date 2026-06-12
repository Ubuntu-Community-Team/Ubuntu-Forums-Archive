---
title: "Ubuntu 7.10 on mac pro 2008"
date: 2008-02-12
forum: Apple Intel Users
---

### Post by agb32 on 2008-02-12
Hi,
am having problems installing ubuntu 7.10 on a mac pro 2008 version (nvidia 8800 graphics card).
I get as far as selecting an install, or safe install, it then loads the kernel, says it is alive, and the screen goes blank.

Can anyone help with this?

Thanks...

---

### Post by agb32 on 2008-02-13
No worries, its now working...
Here is what I had to do:

In OSX, shrink the HFS partition, and leave part of the drive unpartitioned, and then install refit

Then use the TEXT ONLY ubuntu installer (its a different download from the normal installer).

Install your system (from CD).

After installation, when you get to grub, edit, and the line which has "splash" in it, change to "nosplash".

It may then boot fine.

If this doesn't work, you'll end up with a blank screen, but a functioning OS.  However, since ubuntu doesn't come with sshd installed, you'll not be able to connect to it.  In this case, reboot using the install CD, and enter in rescue mode.  This then gives you a terminal where you can apt-get various different software.  

You should probably install the NVIDIA driver (from NVIDIA website), ssh and various other useful things to allow you to poke around in the dark.  Another thing that you could do is:
create an /etc/inittab file containing a line :id:2:initdefault:
Then, in /etc/rc2.d/ change Sxxgdm to Kxxgdm (xx is a 2 digit number) to avoid starting the graphical display (once you're logged in, you can then start it using startx).  

Finally, once you're sure everything is working correctly, you can change the 2 to 5 in /etc/inittab to give you a gui interface from boot...

Hope that helps someone...

---

### Post by rgonzalez on 2008-02-18
wouldn't it be easier if UBUNTU considered to fix this problem with Parallels installations on MAC's ?  I gave up trying quite quickly and I find UBUNTU to be ver nice looking and fair to give it a shot, but it has been impossible to install on my macbook natively or using parallels, so I just about gave it a rest.

what makes software excel is its ability to perform cleanly, so far ubuntu on my macs has not even pass a single installation, that tells me a lot of the implementation, even before getting a single copy to work on any single mac we have.

Sorry, but it's the truth !, once you get Ubuntu working from CD or ISO at the first shot on a MAC, I will certainly continue to give it a try (7.10 ubuntu)

regards to all

---

### Post by cyberdork33 on 2008-02-18
> **rgonzalez said:**
> wouldn't it be easier if UBUNTU considered to fix this problem with Parallels installations on MAC's ?  I gave up trying quite quickly and I find UBUNTU to be ver nice looking and fair to give it a shot, but it has been impossible to install on my macbook natively or using parallels, so I just about gave it a rest.

what makes software excel is its ability to perform cleanly, so far ubuntu on my macs has not even pass a single installation, that tells me a lot of the implementation, even before getting a single copy to work on any single mac we have.

Sorry, but it's the truth !, once you get Ubuntu working from CD or ISO at the first shot on a MAC, I will certainly continue to give it a try (7.10 ubuntu)

regards to all
[LIST=1]
[*]Parallels has nothing to do with this thread.
[*]The issues with installing on parallels is a bug in parallels, not Ubuntu.
[*]Apple, nor several of the hardware manufacturers they use for components in their machines has never had any intention of having Linux operate cleanly with it. Linux developers cannot create "cleanly-performing software" without cooperation from the hardware manufacturers. ie. Closed-Hardware + Closed-Platforms != easy Linux[/LIST]If you expect Linux to run perfectly on something that is not intended to run Linux, then you will be disappointed (as it seems you have been). Ubuntu runs great on hardware that it built to be compatible such as the Dell Ubuntu machines or computers from System76.

---

### Post by 3rdalbum on 2008-02-19
rgonzales: If Ubuntu doesn't run or install on Parallels, please file a bug report with the developers of Parallels by visiting this address: [http://www.parallels.com/en/support/desktop/request/](http://www.parallels.com/en/support/desktop/request/)

Only your bug report will help the developers of Parallels improve their product so that it works with Ubuntu. Ubuntu does work fine directly on real computer hardware and on most other virtualisation programs, so it does look like a shortcoming in Parallels.

---

