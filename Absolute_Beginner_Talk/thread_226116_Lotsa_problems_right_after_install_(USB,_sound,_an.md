---
title: "Lotsa problems right after install (USB, sound, and wireless)"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by esayex on 2006-07-30
Hey, I'm a newbie to linux and stuff. I just installed Dapper Drake yesterday and I faced a slew of problems. (Listed in order of personal importance)

1) No USB support at all
2) Sound card is botched
3) Wireless doesn't work (but LAN ethernet does...)

Computer specs:
Gateway MX6421 (15.4 in screen laptop)
AMD Turion 64 processor, 1.8 GHz
512 MB RAM
ATI Radeon XPress 200M video card
Conexant AC97 Audio
Broadcom BCM4318 [AirForce One 54g] 802.11g
I currently dual-boot Ubuntu and Windows XP Media Center Edition
I also boot Ubuntu with the "noapic" function. In case that matters. It was getting the MP-BIOS bug...

Ok, first things first:

1) No USB support.
I've pugged in 2 different devices and none of them have worked, not the least of which is my Labtech Optical Mouse (Model no. M-UAA103). If it's plugged in at boot, the optical light is on, but it doesn't work. If I plug it in after boot, no light comes up and it still doesn't work.

I've also plugged in a Western Digital 80GB hard drive (Model No. WD800U017-RTN). It's powered by USB. The light comes on (it's getting power) and the hard drive spins, but nothing shows up...

I've also commented out the blacklists for usbmouse. Nothing changed.

2) Sound card is botched.
I mentioned that I had a Conexant card above. Ubuntu thought that I have an "IXP SB400 AC'97 Audio Controller" with the Vendor "ATI Technologies" If I try to play any sounds (including startup sounds) It takes the first second of it and repeats it several times, and does the same with the next second or so. I can mute, but I wanna listen to something sometime...

3) Wireless doesn't work
Ok, I'll admit, I have the POS "Broadcom BCM4318 [AirForce One 54g] 802.11g card." I've scoured the forums and done everything. I've installed drivers through ndiswrapper and put in network manager. Nothin' Doin' I currently have the bcmwl5 driver and not the bcmxx one.

Any suggestions?

---

