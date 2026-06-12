---
title: "Problems with the Live CD... complete newbie!"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by TpyKv on 2008-01-14
Hi Everyone,

This is my first post so please excuse me for being so useless, I will get better over time, I promise!!

I have the Ubuntu 7.10 live CD and I'm trying to get it working on a Sony Vaio NR10E laptop. 

Whenever I try to "Start or Install Ubuntu" it tries to load up but the screen hangs and displays a load of mutli coloured lines.. and does nothing more.

I tried to Start in Safe Graphics Mode - and it works fine. 

The problem is - I don't want to run in safe graphics mode, I want to install it fully. Will it work properly if I choose to install it or will I always have this graphics issue? If so are there any work-arounds? 

Also I need to set up a partition, the HDD is 160GB so I'm thinking of giving 20GB to linux until I know what I'm doing with it - will it be OK to set up a partition now (after the laptop has been used, programs installed & so on) or should I do a clean install of windoze and then make the partition at this time? to keep things clean? 

Thanks for any help you can offer! 

Kind regards,

Kevin

---

### Post by philinux on 2008-01-14
It will work fine once fully installed. It's just that your graphics card will need sorting after the install.

Which card is it?

---

### Post by TpyKv on 2008-01-14
Thank you for the quick reply!

It's the Intel GMA X3100

Do you know how I would go about configuring this after installing?

---

### Post by LeAstrale on 2008-01-14
First of all welcome to The Ubuntu Forums and i hope you enjoy your stay.

The multiple collored bars sounds a lot like a graphics card error. (it does that on my Nvidia 8800gt)
I usually just install from text mode and then fix the graphics problem before booting the GUI.
My usual fix is to set the drivers to "vesa" in the xorg.conf file found in "/etc/X11/" you can edit this file from command line interface using nano as a text editor.

However if you can boot the live cd in safe graphics just install ubuntu, and then well install the graphics drivers afterwards.

---

### Post by thisismalhotra on 2008-01-14
Alternatively, you can download the alternate cd from UBUNTU website..

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Check the box which says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

and then install in text mode, that what I do mostly when I build a new system because things can go funny with LIVE CD, at least always did with me....

---

### Post by TpyKv on 2008-01-14
> **astral-1 said:**
> First of all welcome to The Ubuntu Forums and i hope you enjoy your stay.

The multiple collored bars sounds a lot like a graphics card error. (it does that on my Nvidia 8800gt)
I usually just install from text mode and then fix the graphics problem before booting the GUI.
My usual fix is to set the drivers to "vesa" in the xorg.conf file found in "/etc/X11/" you can edit this file from command line interface using nano as a text editor.

However if you can boot the live cd in safe graphics just install ubuntu, and then well install the graphics drivers afterwards.


Thank you! 

Just as I thought...
I am so new to this I haven't learnt how to install with the text editor yet. 

I've just printed the compete guide to installation so will have a read through this tonight & hopefully get to grips with it. 

I'll come back to this once I've had a play around...hoping it will make more sense then.

Thanks again!! 

> **thisismalhotra said:**
> Alternatively, you can download the alternate cd from UBUNTU website..

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Check the box which says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

and then install in text mode, that what I do mostly when I build a new system because things can go funny with LIVE CD, at least always did with me....

I'd like to try it this way. As soon as I've read enough & plucked up the courage I'll start fiddling with it!

Last time I tried Linux was years ago, on a machine I made myself... nothing was supported and I killed the machine by installing Caldera Linux, from the idiots guide book. Turned out they become SCO and didnt support any older versions so I lost everything.

Ready to give it another go - just need to get it right this time!

Thanks again for your help, will let you know how I get on!!

---

### Post by TpyKv on 2008-01-29
THANK YOU!

Ubuntu is now up & runnng and looking sweet...!

:guitar:

ROCK ON

I'm well happy.

Can't wait to get out of work so I can have a proper play....

---

