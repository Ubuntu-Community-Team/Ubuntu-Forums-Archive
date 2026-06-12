---
title: "Problematic Installation"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by aladdumonk on 2007-05-04
ok, so after getting everything to boot and finally work using the alternate cd, I cannot get through the 'select and install software' portion of the install. It stops at 6% everytime; continues to work for about 15 minutes, then gives an error message. I really do not know what to do. The md5 is good, I've tried using mirrors, not using mirrors, and still I get nothing past 6%. I'm installing on an older HP pavilion with 1.3Athlon. Any suggestions?

---

### Post by aladdumonk on 2007-05-04
anyone??

---

### Post by Terl on 2007-05-04
What is the error message?

Have you verified/checked the cd for errors?  If it is bombing out it could be the cd burn was no good.

What are the system specs of your pc - you gave the cpu, but what is memory, graphics card etc? 

The more info the better when it comes to troubleshooting.

---

### Post by aladdumonk on 2007-05-04
> **Terl said:**
> What is the error message?

Have you verified/checked the cd for errors?  If it is bombing out it could be the cd burn was no good.

What are the system specs of your pc - you gave the cpu, but what is memory, graphics card etc? 

The more info the better when it comes to troubleshooting.

the error is just 'installation step failed'. 256 memory, onboard graphics. this is actually the second cd I burned since the first one was doing the same thing. do you think I should just download again?

---

### Post by Terl on 2007-05-04
How much memory does the pc have?

What kind of graphics card?  Is the card on the motherboard?

It sounds like you may have a system issue.  Post the specs so we can tell better.  :)

EDIT:  Ooops, I see you did post the RAM and graphics info.  If I were you, I would try Xubuntu.  With just 256 megs of ram and an onboard graphics card cutting into that too, I would try the lighter weight distribution.

---

### Post by reckless2k2 on 2007-05-04
Try downloading from a different mirror and try the process over again. 

It may be a hardware issue with the box. Something to consider.

---

### Post by aladdumonk on 2007-05-04
like I said, 256mb memory. And I honestly have no idea what the graphics card is. I know there has never been an upgrade, so it would just be whatever they put on pavilion laptops. 30gb HD.

---

### Post by aladdumonk on 2007-05-04
haha, now downloading from any mirror seems to be down. Fantastic luck

---

### Post by Terl on 2007-05-04
> **aladdumonk said:**
> like I said, 256mb memory. And I honestly have no idea what the graphics card is. I know there has never been an upgrade, so it would just be whatever they put on pavilion laptops. 30gb HD.


Yes, you did.  I apologize I missed it.  I am writing from work right now--got distracted a bit.

Ubuntu requires 256 megs of ram, which, with onboard video you really don't have because the video uses some of the 256.

Xubuntu suggests 128mb ram so it may be a better fit for you and would most likely run better on your pc.  It is available: [Click for Xubuntu]("http://www.xubuntu.org/")

---

### Post by aladdumonk on 2007-05-04
I guess I still don't understand why the programs wouldn't load. This isn't my first shot at linux, and it seems that no matter what computer I try, I always run into some major problem. Oh well. I'll keep trying I guess

---

### Post by Terl on 2007-05-04
I had problems before when I had older pc's.  Sometimes you just need a lighter "weight" (less resources required) distro. 

Did Ubuntu work at all for you?  Did the live cd version boot and run?

I would not give up.  I have had linux on some fairly old stuff like a 133Mhz ibm laptop with 64 megs of ram.  It is all in what you put on it.  I could not run kde to save myself, but it did run fluxbox, xfce, and windowmaker without a problem.

Try Xubuntu.  It uses the xfce desktop (easy to use) and will run leaner and faster for you on your pc.  No need to give up.

---

### Post by aladdumonk on 2007-05-04
New Question. If I simply finish the installation, is there a way to put the programs on it later?

---

### Post by Terl on 2007-05-04
> **aladdumonk said:**
> New Question. If I simply finish the installation, is there a way to put the programs on it later?

Are you going for a server install?  If so, yes you can add more programs later.  What are you shooting for on this install?  Just a working Linux install?  If you are trying for Beryl or compiz I fear they may not work for you.

---

### Post by aladdumonk on 2007-05-04
I just want the full ubuntu, and I can't seem to get anything to go when it comes to programs on the text based installation. I just want a linux to learn on and it seems like this is the way to go since it's the only distro I've found with a solution for netgear wpn111 for wifi.

---

### Post by aladdumonk on 2007-05-04
so I decided to try and verify the cd I'm using. I got this error

'The ./pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.6.3-2ubuntu_i386.deb file failed the md5 checksum verification. Your cd-rom or this file may have been corrupted. '

---

### Post by aladdumonk on 2007-05-04
and when I check the md5 I get this:

ff0cc7c9ed5157f0ff8c0f2213973f49

which I believe is what it should be.

---

### Post by jargoman on 2007-05-04
upgrading your ram to 512megs would be a good solution or as terl pointed out xubuntu

it's not text based and actually not that bad

plus once you get xubuntu up and running you might be able to get away with adding kde after with (make sure your connected to the internet)

$ sudo apt-get update
$ sudo apt-get install kde

it takes about 20 mins or so maybe longer with an older computer like yours.

although running kde with low ram might not be a good idea. 

once kde is installed you logout and before loging in go to options and select session and chose it. You can have many different window managers

---

### Post by talex on 2007-05-04
I am ABSOLUTELY new to Linux installation, etc.  I had the same problems.  I actually got to a point where my installation seemed to work, but still could not boot.

I have 7.04 currently installed on an IMB knock-off, 20g hard-drive, Pentium I with only 128mb of ram.  I ended up using the alternate CD (downloaded), which I finally got to work.  One thing that was also new to me was the image file process.  I used InfraRecorder to burn the image on an XP system.  I finally slowed my write rate to 4x, which took a little while longer, but worked!  

After reading so many posts where write speed was an issue (my originals were at default speed of max), I tried it out, worked much better.

You might try it, hope it helps.

---

### Post by jargoman on 2007-05-04
oh sorry looks like you got an error on your disk check. If you,think your MD5 is correct then try burning again but with whatever program your using to burn it with try to change the write speed to a slower setting

also note that before I wrote that you could add kde after installing xubuntu now I realise that ubuntu's default is gnome and that would be 

$ sudo apt-get update
$ sudo apt-get install gnome

adding kde would result a kubuntu like installation
sorry bout the mix up

---

### Post by aladdumonk on 2007-05-04
no problem, thanks for all the feedback everyone

---

