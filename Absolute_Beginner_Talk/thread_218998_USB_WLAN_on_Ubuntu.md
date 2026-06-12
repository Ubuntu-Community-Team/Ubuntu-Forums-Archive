---
title: "USB WLAN on Ubuntu"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by bwillsher on 2006-07-19
I've got a BlueNext Wireless USB Dongle which I am trying to get to work on a system running on Ubuntu 5.10.

I've used linux before but never installed it myself.

The Linux driver is available from [here ]("http://www.bluenext.co.uk/products/wifidangle.html"). It comes with a very lengthy procedure to install the driver.

Isn't there an easier way?

Also, how do I know if the driver is installed or not? Because it comes up on device manager when I plug it in.

I would be really appreciative if someone could have a look for me.

---

### Post by mattisking on 2006-07-19
Have you considered upgrading to Dapper? Dapper supports many wireless NICs by default without any effort on your part. Just plug it in and it works. That's what I would try first.

Then, I guess I'd try following those directions if I had to.

---

### Post by bwillsher on 2006-07-20
OK, i've installed dapper instead (much nicer) but I still can't figure out how to install drivers!

Is there no easy way like windows xp?

Thanks for any help!

---

### Post by risbac on 2006-07-20
> Is there no easy way like windows xp?

Usually, there are two solutions:

-hardware supported by the distribution, then nothing to do, it's very easy
-hardware not supported, then it's complicated most of the time. 

I check the Linux driver for your USB Dongle, the documentation is nice, but for a beginner, I can't say it's as easy as Windows...

So my advice in your situation: download the windows driver, extract it and save it somewhere (should be a .sys file if I remember well, not so sure), and install "ndiswrapper-utils" + "ndisgtk". This software will allow you to use the windows driver. 

You will then have a new entry in your "system>administration" menu if I remember well. Then you can specify the driver to use (the one you downloaded), and ndiswrapper will tell you if it found the hardware. If it's the case, you are lucky, you should be able to use the dongle. 

My advise to use the dongle once it's installed: install network-manager. It's a much better software to handle wireless connections. 

Hope it helps.

---

### Post by bwillsher on 2006-07-20
I tried using [this]("http://www.ubuntuforums.org/showthread.php?t=31926") guide, but I couldn't install ndiswrapper.

I got version 1.21, will this work with ubuntu 6.06?

When I use the command 'sudo make' it says 'make' is an unknown command.

Any ideas?

---

