---
title: "Question Regarding Kernel w/o Modules"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by parad0x on 2006-01-30
Hi, 
I am a newbie at linux and I need some help for class:
For one of my classes I have to do two things... 

1) Compile a kernel w/ modules and install it
2) Compile a kernel w/o modules and streamline it as much as possible, while still allowing for the computer and all of it's components to function.

I used, the Ubuntu kernel 2.6.12 and completed step 1. The computer runs fine. Now... my question is, with step 2, how do I know what I need and what I don't? I know the specs to my hardware, but when I was running through menuconfig... there were so many options which I just have no idea if I need them or not.  The professor wants it as stripped down as possible.  Is there anyway I can see what modules of my existing kernel are in use by my hardware so I can compile those into the kernel for step 2? If not, how should I go about removing options from menuconfig(all the items I am not sure about).

One more question on the side: any hints or tips on getting a dell truemobile 1300 wireless card to work with ubuntu?

Thanks ahead of time for your help.

- Duncan

---

### Post by mo_x on 2006-01-30
You can see the modules that are loaded with the lsmod command.

---

### Post by wrtrdood on 2006-01-30
As mentioned, the lsmod command is a good place to start.  Try lspci as well.   To build a kernel as described in option 2 you must know your machine very well.  You need a complete list of the hardware currently installed.  Yes, it's tedious.  A good place to start is to copy the config file under /boot and step through every feature listed, removing things you KNOW you don't need on this machine.  Eliminate the excess.  Default kernels usually include everything in the world because there's no good way for the distributor to know what sort of machine the OS will be installed on.  The beauty of Linux is that we can eliminated 80% of this stuff and still have a working system.

The most difficult part about building a kernel that contains all the devices needed is that if you leave any out that are needed (or get too aggressive in your removing), you'll have to go back, add it in, then rebuild.  It can be a time consuming effort but you will learn a lot about building kernels.

Do this: Keep a copy of the default .config file found in /usr/src/linux.  Make additional copies of this same file to another location everytime you change something and rebuild.  It can be very handy when it comes to keeping track of the changes being made and if you mess it up big time, you can easily recover.

Good luck.

---

### Post by az on 2006-01-30
You need udev, an initrd and a bunch of other things to run Ubuntu.  If you are being rated on how small your kernel will be, you may have an easier time by chosing an earlier linux distribution (debian potato or Woody)

They booted with a statically built kernel and did not even use an initrd.


If you want to install debian Woody, pick the bf24 option so that you run the 2.4 kernel.  Then you can dowload the source for linux 2.4.18 and rebuild it with only the modules you need.

Aim low.

...Just a though.... 

Installing Woody can be difficult - you need to set up your partitoins beforehand and load the modules yourself, but I though I would just suggest it.

---

### Post by parad0x on 2006-01-30
Thanks for all the replies :-)

---

