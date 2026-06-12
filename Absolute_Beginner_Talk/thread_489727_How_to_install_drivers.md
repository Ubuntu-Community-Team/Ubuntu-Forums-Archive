---
title: "How to install drivers?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by esl1885 on 2007-07-01
I have downloaded the Linux drivers for my Belkin F5D7010 wireless card, but have no idea how to 
install them in Ubuntu. I am new to Linux, so I need clear instructions. So far, I can't get the wieless
to work at all. If I set my router up for no encryption, it acts like it is getting a signal, in that it shows
the power bars at the top of the screen, but my browser does not connect. If I use encryption, I get nothing (wap or wep). 
If I use a wires connection, it works fine.

Hope someone can help.

Thanks,

Sam

---

### Post by Raineer on 2007-07-01
Would you mind posting the URL you followed to get the drivers?  There are quite a few ways this can be done, typically from a vendor you're getting a script that must be run.  If you can post the URL I'll try to walk you through it.

---

### Post by esl1885 on 2007-07-01
I can't locate the url right now, but the name of the file is RT500-Linux-STA-1.4.6.6.tar.gz.
Will thta help. I searched thru so many places today that I just can't remember where I found it.

Sam

---

### Post by esl1885 on 2007-07-01
Found the link.
[http://www.ralinktech.com.tw/data/RT2500-Linux-STA-1.4.6.6.tar.gz](http://www.ralinktech.com.tw/data/RT2500-Linux-STA-1.4.6.6.tar.gz)

Sam

---

### Post by Raineer on 2007-07-01
Ok the writeup is going to be in the readme file.  This **is** a bit more difficult than your standard driver patch or configure/make/make install setup.

Check under the /module/ directory of your driver for the readme file and take a look through there.  You'll need to know whether you have a 2.4.x or 2.6.x kernel (I'll assume it's 2.6, you can verify by running **uname -r** in a terminal window)

Essentially what they did was place "makefiles" for both kernels in the same driver, although it's no big deal. 

Step 'A' is instructing you to copy the **makefile** and **load** files out of the "2.6.x" directory and into the main directory of the driver you extracted.  This will overwrite whatever it typically uses by default.

Step 'B' has you run **make** against the makefiles to configure the driver. It tells you to include the path to your kernel, this should be *somthing like* /lib/modules/2.6.20-16-generic/kernel.  I'm not 100% sure if the needed source files are included by default on installation, they may have to be requested through Synaptic.

Lastly, step 'C' has you run the program you created with **make**.

Sorry I can't be of more help on step B, have to run and to be honest I'm not 100% sure where to explain the kernel source is located at, hopefully someone else can help with that.

---

