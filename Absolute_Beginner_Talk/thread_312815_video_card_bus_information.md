---
title: "video card bus information"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by johnmxg12 on 2006-12-05
I have an ATI 200m express card, and i'm configuring the xserver-xorg settings, and it's asking for the video card bus identifier.  using the command lspci -x i get 

01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
00: 02 10 55 59 07 00 b0 02 00 00 00 03 08 ff 00 00
10: 08 00 00 c8 01 90 00 00 00 00 10 c0 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 91 30
30: 00 00 00 00 50 00 00 00 00 00 00 00 0a 01 08 00

for my video card information.  i know this is a total NEWB question but what should i type in for my video bus card info??

---

### Post by RAOF on 2006-12-05
Generally, you don't need to care (and I'm pretty sure it says "if you don't know, just accept the default").  Just accept the default :).

---

### Post by johnmxg12 on 2006-12-05
well , the reason why i'm going back to reconfigure my video settings is because i cant get 3d rendering enabled so i'm trying to be as specific as i can with all the settings.  

i've read every single thread on how to configure my video card, haha i'm getting desperate

---

### Post by RAOF on 2006-12-05
Oh, 3d rendering on an ATI card.  Joy. :-|.

I stand by my "just accept the default" answer, though.  It won't affect whether or not you get 3D acceleration.

---

### Post by rajeev1204 on 2006-12-05
hi 

they r right

just accept the default value for these things( things which we dont understand- i went through same procedure when configuring x org.)


just check options for refresh rates and stuff - but mostly defaults will be fine

---

### Post by johnmxg12 on 2006-12-05
I never knew how difficult it would be to configure an ATI card with a well-known operating system. i am absolutely stumped.

---

### Post by rajeev1204 on 2006-12-05
> **johnmxg12 said:**
> I never knew how difficult it would be to configure an ATI card with a well-known operating system. i am absolutely stumped.

i have an nvidia card and i had a bit of a problem too .  but its really not that bad.i hear ati drivers r tricky . but keep posting in these forums and u generally get up and running in a few hours .


regards

rajeev

---

### Post by RAOF on 2006-12-05
**Man**, googling for "xorg ati 200m" gets a **lot** of "it doesn't work pages" :(.

However, the FreeDesktop.org web page has this heartening piece of wisdom:
> IGP

The Radeon IGP chipsets do not have discrete video ram. They share system ram much like the Intel i8xx chips, and VIA/S3 ProSavage/Twister chips. There is support for 2D and 3D acceleration for the IGP chipsets in DRI and Mesa CVS. **There is no 3D for Xpress 200M Northbridge integrated gpus due to undisclosed memory initialisation (july 2006).**


If that describes your card, it's probably time to try the fglrx drivers.

---

### Post by Shatrat on 2006-12-05
> I never knew how difficult it would be to configure an ATI card with a well-known operating system.
Actually, I dont think anyone at ATI has heard about linux yet.  For a long time they only had 1-2 guys maintaining their linux driver, from what little you could gather from release notes and forum posts.  They're trying to improve that now, but they're still light-years behind nvidia.

---

### Post by rajeev1204 on 2006-12-05
hi

i dont know about ATI, but u r right .Nvidia have done a brilliant job of providing excellent drivers . i have a new 7600 gt and i was afraid i will fry it by using in my 64 bit OS . 


In fact nvidia is the reason i have migrated to ubuntu.( or is that linux)!!?

its important for gamers like me

i hope ati get their act together . I  feel with AMD buying ATI , stable drivers are very close for ati owners

regards

rajeev

---

### Post by johnmxg12 on 2006-12-05
yep, i've tried the fglrx drivers, i've tried everything. this is the only thing i dont like about switching to Ubuntu, everything else is awesome.  configuring the video card is a whole different ball game

---

### Post by rajeev1204 on 2006-12-05
hi
john , i suggest u dont try 'everything' or maybe u could damage the card. i read on the forums somewhere about a workaround for ATI 200 graphics.

just search for it in the forums .i think they may have some new driver  out at their website .




regards

rajeev

P.S hang in there.

---

### Post by johnmxg12 on 2006-12-05
so i went to the ati driver web site, and i went to my section of video card.

i tried to run check.sh both in the normal terminal and as root and i got this 

-e =====================================================================
-e  ATI Technologies 
-e =====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.

and i downloaded the driver, and tried running that and i got this: 

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.29.6.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 176: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

any thoughts?

---

### Post by rajeev1204 on 2006-12-05
hi

maybe this will help [http://ubuntuforums.org/showthread.php?p=1837411]("http://ubuntuforums.org/showthread.php?p=1837411")

---

