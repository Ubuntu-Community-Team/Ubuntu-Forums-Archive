---
title: "Fresh ubuntu installation - two problems"
date: 2008-03-14
forum: Apple Intel Users
---

### Post by nylock10 on 2008-03-14
Hey there,

I just installed the latest version of Ubuntu on my Intel iMac (first generation Core Duo 2GHz, 2GB RAM, Mobility Radeon x1600 256MB).

Everything worked fine,  except for two things I'd like to solve:

**a: I cannot find any wireless networks (needs drivers? I need to connect to my WPA-secured Airport network**)

and...

**b: I do not have any graphics support for my video card (I'm assuming I just need to install the drivers)**


How can I get wireless to work and graphics support?

Thanks :)

---

### Post by cyberdork33 on 2008-03-14
What version do you mean when you say "latest"?

You need ndiswrapper for wireless. This is for the Macbook, but you should have the same card:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b)

You need to install the proprietary drivers for graphics. If you are on Hardy, you use the driver manager (in system > administration), if you are using gutsy, try envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by nylock10 on 2008-03-14
I'm using "Gutsy", sorry for not mentioning that in my previous post.

If that Dell driver in the MacBook Wireless guide doesn't work, should I try using the wireless driver from the Leopard DVD? I'm not totally sure if my iMac uses the same card as the MacBook, my iMac has an 802.11g-based card as opposed to the Santa Rosa MacBook's 802.11n card.

Using envy to get my graphics card going looks like it'd work, thanks :D

---

### Post by alphabyte on 2008-03-14
did you use the 1383 version? I have the exact same macbook 1st generation and didn't have that problem.
-Alphabyte

---

### Post by nylock10 on 2008-03-14
I used the version that came with my Ubuntu 7.10 Gutsy CD, I'm not sure what build number it is though.

I followed the guide to enable wireless, but it didn't work. I still cannot connect to my network (I couldn't even see it).

I tried installing again, but Terminal said the driver was already installed - so the installation must have been successful.

Could it be since I'm using a WPA-protected network that the security is causing the problem?

**-edit, I got wireless working-**

I followed the following guide and after rebooting I got wireless and successfully connected to my WPA Personal-encrypted network:

[http://ubuntuforums.org/showthread.php?t=706034](http://ubuntuforums.org/showthread.php?t=706034)

Time to try to get the graphics card going.

---

### Post by cyberdork33 on 2008-03-14
> **alphabyte said:**
> did you use the 1383 version? I have the exact same macbook 1st generation and didn't have that problem.
-Alphabyte
Don't know what you are talking about... and he doesn't have a Macbook.

It is the same broadcom hardware in your iMac.

Good luck with the graphics drivers.

---

### Post by nylock10 on 2008-03-15
Envy worked, I get graphics acceleration now.

Thank you :KS

---

### Post by alphabyte on 2008-03-15
> **cyberdork33 said:**
> Don't know what you are talking about... and he doesn't have a Macbook.

It is the same broadcom hardware in your iMac.

Good luck with the graphics drivers.

Yea I miss read that as something else, my bad :guitar:

---

