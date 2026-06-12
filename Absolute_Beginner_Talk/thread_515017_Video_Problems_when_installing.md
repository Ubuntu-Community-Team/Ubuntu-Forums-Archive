---
title: "Video Problems when installing"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by MarkSparks on 2007-08-01
I'm trying to get rid of Vista off my PC and install Ubuntu 7.04 on the following machine:

 	 AMD Athlon 64 X2 4600+ Windsor 2.4GHz Socket AM2 Processor Model ADA4600CUBOX - Retail
 	 GIGABYTE GA-M55SLI-S4 Socket AM2 NVIDIA nForce4 SLI ATX AMD Motherboard - Retail
         G.SKILL 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop 
         EVGA 320-P2-N811-AR GeForce 8800GTS 320MB 320-bit GDDR3 PCI Express x16 

And my monitor is a Dell 2405fpw 24" LCD using the DVI connector. 

I can get to the menu screen where it asks me to run the live boot CD and install , but when I go with that option, the screen goes black and never comes back. After about 5 mins, I can tell that it's in the Live CD cause I can use the power switch to shut down the PC gracefully (kinda at least the ACPI way). 

The only thing I read was to use f4 at the live boot menu and select a resolution. My monitor natively wants to use 1900x1200 60hz. 

I tried the safe mode but not this F4 yet, any other suggestions for me to try tonight when I get home?

Any help would be greatly appreciated. 

Mark

---

### Post by Rocket2DMn on 2007-08-01
Been seeing a lot of similar threads this morning.  You may need to install with the alternate cd, a lot of people tend to have problems with the LiveCD, esp. using DVI.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and select the alternate desktop cd checkbox at the bottom.  This will give you a text based installer, not a live session, which doesn't require the Xserver which is the source of a lot of video woes.
Don't forget to check the md5sum
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
and burn at a slow speed, like 4x, to prevent write errors.

You could try plugging in with VGA and trying the LiveCD that way, then using the DVI later, but I'm not sure if that will work during install.

---

### Post by Sayers on 2007-08-01
Eh, That is a brand new Video Card :) , There should be drivers soon.

---

