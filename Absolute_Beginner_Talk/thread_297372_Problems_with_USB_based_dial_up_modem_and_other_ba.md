---
title: "Problems with USB based dial up modem and other basic questions"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by ryalt on 2006-11-11
Hello.

**opening:**
I guess I'm fairly new to linux and ubuntu in general, and after trying endlessly to try and figure out my problems on my own for the last couple weeks, I'm now coming to you guys for some help.

I've come to the conclusion that my skill is basically that I can use it, but I don't know it, and from moving from windows like I am doing, not knowing how to fix things is very frustrating.

**problem #1:**
I currently am not able to connect to the internet using the Ubuntu/linux operating system.

I use dial up on my computers (archaic I know) and while it is not by choice, it's the only thing I have available.

I do not have a serial modem or hardware modem to install, what I have been using for the last year or so is a USB based dial up modem, and linux does not seem to want to recognize it easily. I don't know how to make it work, and that's my largest problem.

So the question is: How do I get linux (ubuntu) to recognize my USB modem so that I may use it to connect to the internet?

**problem #2:**
And another horror being, I use AOL to connect to the internet (which is paid for me, once again it's not my personal choice for best connection).

I was trying to look up ways to use the basic linux things to connect, but I guess I've pretty much only just installed the software, and let AOL do its thing to connect, I haven't got into the minor details of it.

The question being: How can I connect through AOL onto the internet using Linux? Can I install the software and will it run properly, or do I need to go about it in a completly different manner?

**thanks:**
I just wanted to state a thank you in advance. Trying to get the computer to connect to the internet has been a huge pain, and not being able to download any of the software updates or codecs is really killing me (I just want to listen to MP3's and figure out how to make WoW work damn it lol.) So thank you in advance.

-Ryalt

---

### Post by ryalt on 2006-11-11
/bump

please someone say something. :/

---

### Post by gargoyle on 2006-11-11
Sorry to say you problem is that your USB modem is a Windows soft modem just packaged in a different way.

Chances of getting it work properly are slim to none.

However look at the link on modems listed below.
[DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")

Maybe you will be able to get it going with information provide there. I am also on dailup and use an external modem from US Robotics, it is a hardware modem serial type. You might be able to pick one up fairly cheap on ebay. $6.00 to $20.00.

Sorry I can not help you with your AOL problem.

---

### Post by christhemonkey on 2006-11-11
For AOL dialup on linux, you will need to use penggy.
It is software for enabling you to connect to AOL with their propreity connevtion.

(its not been updated in a while, but neither has dialup, so you never know!)


If your using edgy 6.10 get the packages from here:
[http://packages.ubuntu.com/edgy/net/penggy](http://packages.ubuntu.com/edgy/net/penggy)
(remember to get all the dependencies such as libqthreads-12)

Then follow a howto such as this one for setting it up:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html)

(you can skip to step 3!)

---

### Post by autocrosser on 2006-11-11
There are some USB modems that work "out of the box"---but not many--The older Zoom Modems work-29xx series--I normally look at:
[http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/)

for information on what "might" work--also look at:
[http://start.at/modem](http://start.at/modem)  (and tic the "mirror site")
[http://www.linuxsecurity.com.br/info/unix/winmodem.html](http://www.linuxsecurity.com.br/info/unix/winmodem.html)

---

