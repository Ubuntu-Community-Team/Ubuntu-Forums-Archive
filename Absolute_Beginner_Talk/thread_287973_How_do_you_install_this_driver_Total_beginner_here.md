---
title: "How do you install this driver? Total beginner here"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Buecai9ahd on 2006-10-29
I need to install this driver for my WiFi USB dongle to work for the tinternet but I dont understand any of it. Goes on about compiling kernels or something then editing stuff, very confusing.
Just installed my first Linux on my PC today so any helps appreciated.
Can anybody give me a shove in the right direction at least?
The driver installation guide's here: 
[http://sms2006.wordpress.com/](http://sms2006.wordpress.com/)
and this is where the original thing came from:
[http://www.bluenext.co.uk/products/driver/wifidangle/Linux.zip](http://www.bluenext.co.uk/products/driver/wifidangle/Linux.zip)
How do I know what version my kernel is aswell?
Thanks for any help you can give to a noob.

---

### Post by Malakia on 2006-10-29
Type uname -r in the terminal and that will tell you what your kernel version is. You should also check the Ndiswrapper website and Madwifi to see if either of them support you wireless card. I have to use ndiswrapper myself to get my wireless working right.

---

### Post by Bachstelze on 2006-10-29
This will be really tedious... Could you paste the output of *lsusb* while your wifi card is pluged in ? Maybe it will work with ndiswrapper, which is way easier to install.

---

### Post by mahy on 2006-10-29
Check this (or similar threads) out:

[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

Good luck!

---

### Post by Buecai9ahd on 2006-10-29
Thanks for your replies guys.
Okay I tried that Ndiswrapper site and Madwifi and my card wasn't on there.
I typed lsusb and this is what it said, if it helps.
Bus 003 Device 002: ID Oace:1215 ZyDAS
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

And mahy, I went to that guide and you had to type commands in to download or update something which I can't do without the internet! What should I do?
Cheers guys

---

### Post by mahy on 2006-10-29
> **sms_sms said:**
> And mahy, I went to that guide and you had to type commands in to download or update something which I can't do without the internet! What should I do?
Cheers guys

Most of those things should be on the installation CD. You'll have to download the rest in windows if there's no other way, via www from packages.ubuntu.com

And make sure to check this: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

---

