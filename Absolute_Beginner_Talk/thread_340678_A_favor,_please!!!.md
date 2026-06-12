---
title: "A favor, please!!!"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by je1117 on 2007-01-17
OK, I'm still having a lot of trouble getting my video to work correctly. What I am asking is for someone experienced who has AIM or something to walk me through what exactly i should do. I've had 5 different people tell me 5 different ways and I would like one person that I can ask questions as they arise.

I've just reinstalled Ubuntu for about the tenth time on a brand new hard drive. I'm ready to go. I haven't installed the updates yet, its a clean install for Dapper. PLEASE, someone help me.

And if no one wants to do that, I guess I would like to ask, what am I running right now? I don't know what xorg, xserver, fglrx, AIGLX, ATI Proprietary are EXACTLY. I need some clarification I guess, is what I am asking.

Thanks again guys.

---

### Post by ithockeytech on 2007-01-17
Hello ,

I am still fairly a newbie, but I will offer what assistance I can.

OK, I'm still having a lot of trouble getting my video to work correctly. 
Q: What is the problem?
Q: What is the specification sheet and model of your video card? 
Q: What are the symptoms when you install.

Please be as descriptive to your issue as possible.

ithockeytech

---

### Post by je1117 on 2007-01-17
OK, I had posted last night about it, but nobody answered really. But i would love to explain it again.

The problem I am having is that I am running a radeon 9200 video card. And when I try to install the Linux proprietary drivers, or fglrx (I think), my system won't boot on restart. It loads everything to the blinking cursor in the top-left of the screen. Then my monitor goes into standby. No sounds, no clicking.

When I try the recovery mode, I try and type commands and it just gives errors every time I hit a keystroke, Even if I get a full command in before it gives an error, it doesn't recognize the command.

---

### Post by Hendrixski on 2007-01-17
Ouch, sounds like another victim of proprietary crap.

Sounds like those drivers hozed your kernel.  Remember they're closed source so they do things to your kernel and nobody on the Kernel development team,  not even Linus Torvalds, know what exactly they are doing, and how to compensate for it.

---

### Post by je1117 on 2007-01-17
Well I download the package.run from the ATI site, and I compile it myself, creating several *.deb files to run. Is that still a closed source file?

---

### Post by phossal on 2007-01-17
> **je1117 said:**
> OK, I'm still having a lot of trouble getting my video to work correctly. What I am asking is for someone experienced who has AIM or something to walk me through what exactly i should do. I've had 5 different people tell me 5 different ways and I would like one person that I can ask questions as they arise.

That's called tech support. It's $100 hour. We all *wish* we had *that* guy for our problems. lol

---

### Post by chipdip on 2007-01-17
> **je1117 said:**
> Well I download the package.run from the ATI site, and I compile it myself, creating several *.deb files to run. Is that still a closed source file?

Well, if you compiled it yourself, no.

---

### Post by happy-and-lost on 2007-01-17
What do you need to use your card for? Personally, I find AIGLX does the trick on my card for 3d apps, DVDs, Beryl... [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) worked for me.

---

### Post by je1117 on 2007-01-17
happy-and-lost, that link looks great, except that I am running Dapper! Will it still work?

I would like to use my card for 3d accelerated games and the such.

---

### Post by happy-and-lost on 2007-01-17
Don't see any reason why it wouldn't work.

I'm running NeverWinter Nights on mine, with no issues whatsoever (It's much faster than it is in Windows too ;)), so I should imagine the same could be applied to yours.

---

### Post by je1117 on 2007-01-17
This is all that is in my /etc/X11/xorg.conf file. This doesn't look right......



Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
"/etc/X11/xorg.conf" 145L, 4422C                              1,1           Top

---

### Post by je1117 on 2007-01-17
I've also noticed something common when i update.

If I got to "Computer," it used to show a "root volume" and my swap. But after I updated it only shows one "filesystem" that is my root volume...except it doesn't label it. And it doesn't seem to recognize it all the way. AND my swap is missing.

---

### Post by PurplePenguin on 2007-01-17
> **je1117 said:**
> Well I download the package.run from the ATI site, and I compile it myself, creating several *.deb files to run. Is that still a closed source file?

I doubt you compiled it yourself... it's a closed driver, the source isn't available.

---

### Post by ljpm on 2007-01-17
Hi le1117,

You said that your monitor worked well before you tried to install the proprietary driver and that the monitor goes into standby when you reboot. From this I am assuming that you have a flat panel monitor. (I had the same problem when trying to install an ati driver) I was able to see the screen by unplugging the flat panel and plugging in an old CRT monitor. Your driver installation may have set the resolution to a value that exceeds the safe operation range of your flat panel so it suts off.

I can't help more with out more information. Please respond if above assumption is correct and if you have a CRT monitor around that you can plug in. As well as details of the exact procedure that you used to install the driver.

---

