---
title: "Wireless ramains a problem ..."
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by CasPol on 2007-12-18
Hi there;

I have the following wireless card in my ACER 3000 laptop

Broadcom Cooperation BCM 4318 (Airforce One 54g) 802.11g wireless lan controller (rev02)

Thanks to a lot of help fromn a lot of people I had it working on one occasion. I was advised to use Wicd, which did work also on one occasion. 

That was it. I can now no longer connect and somehow my card is nolonger being detected. Also it seems that Ndiswrapper has disappeared.

I have been told that I should re-install everyhting from scratch ....

How do I do that ?

---

### Post by Nano Geek on 2007-12-18
Why not just follow those instructions that got it working the first time?
But yes, wireless is still tricky in Linux. Next time you buy a laptop, buy a Intel wireless chip. They work better in Linux.

---

### Post by lswest on 2007-12-18
well actually i have a broadcom, and it's the 4311, which is pretty easy to set up.  just basically ndiswrappered the bcmwl5 drivers and it works.  not sure if it would work for the 4318, but it's worth a shot.

---

### Post by CJ56 on 2007-12-18
I've got an old Dell Inspiron with a Dell 1350 wireless card which uses a Broadcom chip. I got it to work like this - 

I started with a clean install of Gutsy 7.10. I also had to use a wired ethernet connection to get the downloads I needed.

Once I'd installed Gutsy and got to first boot-up, I opened the Restricted Drivers Manager. I ticked the enable box for the wireless card; Gutsy then offered to download the necessary drivers to get the card working. 

I then downloaded Wi-fi Radar from Synaptic (make sure you've enabled & updated your universe and multiverse repositories first).  Wi-fi Radar appeared in the Internet section of the Applications menu. 

After that, I unplugged the wired ethernet. I opened up Wi-fi radar, which picked up and listed all the local connections. I picked the one we use in this house, told Wi-fi Radar to configure itself (choosing Auto in all possible drop-down menus). After a bit of thought, it connected & now works well.

It worked for me, anyway... ;)

---

