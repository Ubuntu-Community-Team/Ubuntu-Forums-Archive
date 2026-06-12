---
title: "Nvidia graphic card isnt working with desktop effects"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by jon peona on 2007-11-28
when i try to use desktop effects on my computer it say "Desktop effects could not be enable", i have try almost everything to get it working, i have an Nvidia gforce fx5200 can somebody please help me ??

---

### Post by freesitebuilder on 2007-11-28
How much RAM have you got?

---

### Post by jon peona on 2007-11-28
512!

---

### Post by linuxlizard on 2007-11-28
I've used 4 different nvidia over the years and they all work great. I've never had near the top of the line either- usually near the bottom or middle. I'm pretty sure my Mom's computer has that card and I set her up with kubuntu fiesty fawn and beryl and all the 3d bells and whistles are flying even though she's only got 256 m ram on an amd athlon 1800+cpu with a 4x agp card.

Nvidia is *THE* video card to use with linux. No other brand is as well supported, with linux drivers coming directly from nvidia itself for years now. I guess because of that, I hate to see people raggin on them when it's probably the user's fault it isn't working.

Have you installed nvidia's proprietary driver? Are you sure? Check in System-Administration-Restricted Drivers Manager.  (You get a warning on ubuntu when doing it- it will say ubuntu doesn't support the software, it's from a 3rd party and some such. Ignore it- all it really means is ubuntu didn't write the driver and can't modify it because it's proprietary from nvidia).

If it's enabled there, and you can't get 3d desktop settings working, you may want to uninstall it there and do it the old fashioned way (go to nvidia's website, download the driver and readme file, and follow the instructions in the readme file).

---

### Post by Znort_Ubern00b on 2007-11-28
ensure you have the correct update on your nvidia drivers

i am using a 5200 card with 1 gb RAM and have no problems with any of the desktop effects

have you checked that the restricted drivers option is checked???

---

### Post by Riffer on 2007-11-28
There has seemed to be issues around nVidia and Gutsy.  There has been tons of post of freezes and lock ups since Gutsy release.  

It seems that the latest beta drver (169.04) fixes these problems.  You can only get it at the nVidia site.  Try that.

---

### Post by firstcupoffreshpressed on 2007-12-04
I'm having the same problem with an nvidia fx 5200 ,64 MB card.  I can't enable desktop effects and the nvidia control panel is only reading 32 mb of ram.  This is a used dell inspiron 5150 I just bought.

I tried using envy and screwed up my screen resolution and finally just did a clean install.  I tried enabling desktop effects again after installing adn enabling the restricted driver again with the same result.

The fx 5200 wasn't nvidias greatest.  I read where the best nvidia engineers were off working on microsoft xbox the year it came out.  Anybody else having this problem?

---

### Post by Fixman on 2007-12-04
Have you tried system->administration->restricted driver manager?

---

### Post by lswest on 2007-12-04
I've got an Nvidia MCP67M chipset in my laptop, and my only issue was a lack of a driver before Gutsy, but now it works fine, and effects are a go.  and my PC has an ATI card, which actually has more issues with Ubuntu:P  however, its an old AGP 9600XT, so that might have something to do with it.  however, the nvidia driver solved any of the issues i had with the nvidia card (its a shared-memory card, 64 ded, up to 560 MB shared) and it works fine now.

---

### Post by SuperMike on 2008-01-23
> **lswest said:**
> I've got an Nvidia MCP67M chipset in my laptop, and my only issue was a lack of a driver before Gutsy, but now it works fine, and effects are a go.  and my PC has an ATI card, which actually has more issues with Ubuntu:P  however, its an old AGP 9600XT, so that might have something to do with it.  however, the nvidia driver solved any of the issues i had with the nvidia card (its a shared-memory card, 64 ded, up to 560 MB shared) and it works fine now.

I've got an HP laptop with the MCP67M Nvidia chipset in it too. As a web developer, I need to keep Windows Vista on it so that I can do IE 7 testing, and then I load Ubuntu 7.10 in a VM with Virtualbox. So far, not so good with the video. All I can eek out is 800x600. I've tried the nVidia binary X.Org driver and it didn't help -- fell back to failsafe with the vesa driver.

---

### Post by fxrocket on 2008-02-06
Sorry for the Hi-jack, but I wanted to share.
I have an AMD 1.4 with the 5200, and I have the twin view working well and still cant get the visual effects to work?  I know it sees the driver, it has to for the twin view to work...yet no luck

---

