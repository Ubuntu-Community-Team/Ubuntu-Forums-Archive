---
title: "Graphic Card and Usb sound card"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by whitethorn on 2007-11-07
Hi, I've been using Gutsy or the past 2 days now, I've managed to set up my Wireless card, but now I'm kinda stuck.  I can't find or figure out how to set up my usb sound card, and my I would like to get my graphic card working with 3d features.

I have a Dell Inspiron 8600 with ATI Mobility Radeon 9600 Pro Turbo. When I click on the Restricted Drivers Manager, I have a ATI accelerated graphics driver when I try to enable it says the  xorg-driver-fglrx isn't enabled.  I tried downloading  xorg-driver-fglrx from the add/remove application and it says

Canonical Ltd. provides technical support and security updates for ATI binary X.Org driver
ATI binary X.Org driver cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

My USB sound card is inside a Toshiba Multimedia Center - Audio/USB Hub, I think there's a Creative Live 24 bit card inside along with a usb hub. I have an external harddrive plugged in and Ubuntu recognizes it, it also recognized that there's a usb sound card.  At first I was able to get sound from it, but only at the test menu (system -> preferences -> sound. I clicked on USB sound and test.  I got a buzz sound. As soon as I tried playing an MP3 or a movie, the playback came from the speakers on my laptop. After setting up my Wireless card, I can no longer get any sound out of my usb card.

So any hints would be great.

Julian

---

### Post by SpiritIsReality on 2007-11-07
howdy
Does this help with your graphics ?
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
trails

envy recommended here
[http://ubuntuforums.org/showthread.php?t=605735](http://ubuntuforums.org/showthread.php?t=605735)
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by whitethorn on 2007-11-07
So I tried the first link, it's working well.  Thanx for the help, now I have Direct Rendering and can use 3d I believe.  I still don't quite know how to make use of it, but I'll figure it out soon enough.  Any ideas how I can maybe get my USB sound card working?

---

### Post by SpiritIsReality on 2007-11-08
howdy.
See if you can find out more certain info about your usb sound card.
Maybe xp will tell you something.
Some have said they don't believe Ubuntu's detection of the card identified like yours.
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org++%22Creative+Live+24%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org++%22Creative+Live+24%22&btnG=Google+Search&meta=)
Can you open the usb case and look at the chip for a positive id?
at google.com type in
site:ubuntuforums.org "your card model" "your card chip" usb 
or different combinations of them, and alone, and see what you can find out.
try runnin' at google.com linux "your card info"
check out the manufacturer's web page, or a retailer who lists it for sale or ?
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound) the OldSoundCard link helped me. snd-cs4236 .

Comprehensive Sound Problem Solutions Guide 
[http://ubuntuforums.org/showthread.php?t=407092](http://ubuntuforums.org/showthread.php?t=407092)

then, there sounds like there could be a conflict between your sound usb card and your wireless card, but hopefully not.
could try googlin' "your wireless card id" "your sound chip" 
and see if you spot anybody with the same combination?

hope'n 
trails

---

### Post by whitethorn on 2007-11-08
I haven't been able to get the card open, I'm going to bring the card back to the store. The microphone and Line In plug don't work anymore under windows so I'm gonna buy a different one for the money.  I think I'm gonna get myself a Aureon Terratec 5.1 MK2. I checked out a couple of the links and I found a page on some wiki which stated that Alsa_snd_.. something supported the card pretty well, so that should be it.  Now I just gotta wait until I get my new card which should be next week sometime.  I'll post another reply once I'm that far.

Thanx for the help.

Oh and I got the Desktop Cube working with cubiz.  Cool stuff!

---

### Post by SpiritIsReality on 2007-11-08
howdy
That's the spirit ! 
trails

---

### Post by SpiritIsReality on 2007-11-08
howdy
If you're goin' to town, have a look at this maybe [http://ubuntuforums.org/showthread.php?t=484846&page=7#post3726136](http://ubuntuforums.org/showthread.php?t=484846&page=7#post3726136)
I'm using a pentium II and it's running like a pentium III, haha !
Sometime this winter, we're hopefully getting a dual core processor computer
to use as a server. Then these clients will sing !
trails

---

### Post by LindsaySlater on 2007-11-21
Hi there, I'm having the same problems, but my mouse does funny things, as well... Oh, and none of my other network cards work... This Hub thing is also a USB network card... If it didn't work so well for me under XP, then I would take it back, perhaps to get a 5.1 sound card... But I just might have to try it out some more... As long as someone else is having the same issues, I don't feel quite so bad.
LS

---

