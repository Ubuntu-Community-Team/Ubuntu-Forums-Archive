---
title: "live cd connecting to internet"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by scottym on 2008-03-15
Knowing what a pain it can be to connect a modem to the internet with Ubuntu, I decided it would be prudent to test my modem on the desktop with live cd. Well, for one day now I have been trying without success. I downloaded the conexant drivers but Gutsy won't recognize the modem. Can any one help please.

---

### Post by Shazaam on 2008-03-15
Dial-up? Is it an HSF or HCF Conexant modem?
Unfortunatly I haven't heard of anybody being able to get an internal Conexant chip dial-up modem working with the livecd.

---

### Post by scottym on 2008-03-15
It is dial up. It is an hsf and I am using the hsfmodem_7.68.00.07full_k2.6.22_14_generic_ubuntu_i386.deb.zip driver,

---

### Post by Shazaam on 2008-03-15
Ahh the Dell driver correct? Kudos to Dell for making a free driver available.
If and when you install Ubuntu the first thing to do is to go to System>Administration>Software Sources and uncheck all of the sources but the cdrom then go to synaptic hit reload. Then install build-essential. Once that is installed recheck the sources and then install the Dell driver.
If it's the driver from linuxant extract the file to your desktop and then install it. I hope you didn't pay linuxant for the driver.

---

### Post by scottym on 2008-03-15
No, I haven't paid for the driver. I have Gutsy exclusively on my laptop and went through a lot of growing pains geting online with the modem. Wireless was another story but finally worked. Not Ubuntu but my lack pf knowledge with wireless connections. I want to have just Ubuntu on the desktop  but wanted to be sure I could connect. You seem to be intimating that if I install Ubuntu, I will be able to connect. Is that so ? I am installing a dual boot to see if I can connect and if so then I will reinstall with just the Ubuntu OS.

---

### Post by Shortspan on 2008-03-15
I'm not sure if this helps, but I used to use a modem with live cd's for about a year before I  got adsl.  However,  I used an external "serial" modem.  I couldn't get my 2 internal modems to work so I went out and bought a cheap, used external (Actiontec 56k).  And you should know that it is faster than either of my internals ever were.  In Puppy Linux there is a setup (for serial modems, at least) that is fairly staightforward if I remember correctly (it automatically finds it, I think).  In Ubuntu or Mint I had to use the termimal since I never did find any other program to get it working.
By the way if you are going to use the program just for the internet, you should consider Puppy Linux.  It is fast even from Live CD because its small enough to load onto and run directly from your RAM.  Once loaded you can take the Puppy Cd out and away you go.
But, for internal modems, I have read in these forums where some have had success but there have been many failures as well.

Michael

---

