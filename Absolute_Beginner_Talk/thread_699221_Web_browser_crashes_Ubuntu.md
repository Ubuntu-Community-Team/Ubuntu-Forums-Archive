---
title: "Web browser crashes Ubuntu"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by K0ivu on 2008-02-17
Hi,

I have a fresh installation of Ubuntu 7.10.
I have only added Opera web browser and Ubuntu updates.

First I used Firefox for browsing, but every ones in a while it suddenly crashes. The mouse cursor is still moving, but I cannot click any buttons or anything. I even cannot exit the browser or use other applications, or do anything with my computer. I only can move the mouse.

So I thought it is a Firefox problem and I downloaded Opera. Exactly the same thing happens with Opera.

Any ideas what to do? It's pretty annoying, because I know even while writing this message that my browser can halt at any moment. And if it does, I have to shut down my computer, switch it on again, and write this message again.

Thank you!

---

### Post by agurk on 2008-02-17
It might be a flash bug biting you. I have better success using the latest flash [here](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux) (grab the .tar.gz, extract, replace /usr/lib/firefox/plugins/libflashplayer.so). To check what version you are currently running, type about:plugins in the url bar.
Oh, and I use the [NoScript](http://noscript.net) add-on to prevent flash from running on most sites I visit.

---

### Post by Prisma on 2008-02-17
i have the same problem. My Firefox crash every time I search something on this forums. Its irritating for me.

---

### Post by jan quark on 2008-02-17
try web browser
kazehakase

it is very slim and stable
i use it and had never issues with it

you can also search the launchpad service for known bugs in firefox

[http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

### Post by K0ivu on 2008-02-17
I tried Kazehakase. It worked fine for pretty long time, but then it crashed OS also.
I think that next I'm going to close all web browsers and use some other applications for a while. If the problem occurs, then it's something else crashing the computer than the web browser.

---

### Post by K0ivu on 2008-02-17
Ok, it is not the web browser. I was looking at desktop properties and suddenly it crashed. It crashed just like I mentioned in the first post: mouse cursor moves, but that is all I can do.

Could this also be a hardware problem? 
Before Ubuntu there was an XP install in the computer, and it never crashed the same way though. 
Is there any system diagnostic tools for Ubuntu (like Lavalyst Everest for Windows)?

---

### Post by agurk on 2008-02-17
Is the computer responding to keyboard commands - can you log out by pressing Ctrl-Alt-Backspace?
Does it help to turn off compositing in System->Preferences->Appearance->Visual Effects?

---

### Post by K0ivu on 2008-02-18
> **agurk said:**
> Is the computer responding to keyboard commands - can you log out by pressing Ctrl-Alt-Backspace?
Does it help to turn off compositing in System->Preferences->Appearance->Visual Effects?
No, computer doesn't respond to anything. Mouse cursor moves, but windows or OS cannot be closed (except by pressing restart or shut down on the computer). 

I turned off the compositing, and it hasn't crashed (at least not yet) while working with the desktop. But it has crashed during Battle for Wesnoth - game session.

Could it be a graphics card driver problem? 
I have His Radeon Excalibur 9600 128MB graphics card. I installed the latest drivers by enabling ATI accelerated graphics driver from System/Administration/Restricted Driver Manager, but I encountered problems. Enabling works ok, but after reboot screen resolution is 800x600, when it should be 1280x1024. It can be changed only to 640x480 when ATI accelerated graphics card driver is enabled.

Also, if the acceleratded graphics card is enabled and I reboot, just before Ubuntu opens up, there comes this 800x600 (or 640x480) resolution GUI that says something like "Ubuntu is running on a low screen resolution mode". I can set the screen resolution from there, and I can select the driver for my graphics card, but after that when Ubuntu opens up, the screen resolution is still only 800x600. And I cannot change it any higher.

If I disable the ATI accelerated graphics driver and reboot, Ubuntu starts up with 1280x1024 resolution.

---

