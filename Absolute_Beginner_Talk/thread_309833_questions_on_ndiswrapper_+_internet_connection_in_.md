---
title: "questions on ndiswrapper + internet connection in general"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by towync on 2006-11-30
Hi everyone:

I just installed Kubuntu 6.10 on my desktop today, and I'm a complete newbie to linux :o . This thread is actually about setting up wireless adapter for internet under kubuntu in general, and it might be a bit long to read, but thx in advance:cool: :

I'm trying to hook up my usb dlink wua-2340 wireless adapter so I can gain internet access for desktop but I'm not exactly sure where to start at all.

(Without that wireless adapter working my desktop cannot connect to internet in any other way. And I can only use my windows xp laptop to surf around for tips on the internet.)

I've played around the system and googled for awhile to know ("to know" might just be too strong a word to describe the state of my awareness of what to do lol) that I probably need "ndiswrapper" before I can try installing the driver for dlink. (I'm not even sure if ndiswrapper already comes with my kubuntu cd, which I made from downloading kubuntu 6.10 to my Laptop, then making a bootable cd for the desktop)

So to get ndiswrapper, I went online and downloaded "ndiswrapper-1.30.tar.gz", copied that onto a blank cd in window xp home, and then popped in this cd to my kubuntu desktop, copied "ndiswrapper-1.30.tar.gz" to the kubuntu desktop, clicked it to unzipp it to /home/computer/ndiswrapper-1.30. 

But now when I type in "ndiswrapper" just like that in command prompt ("K start button" -> "run command" with run in terminal window option checked), I get /bin/sh: ndiswrapper: not found error message. 

I got stuck here and I'm not sure how to proceed.

Other info: lsusb does find the dlink adaptor hookedup (how I wish that itself meant I can start internet lol). Also, if I'm totally off track to achieve the final goal of connecting to internet through my wireless usb adaptor, please enlightened me to other ways, thx so much :) (I looked up a list of supported adaptors for ndiswrapper, and the one I have is listed, but if tihs one doesn't work I can just buy another wireless adaptor, but I'd probably still need ndiswrapper working)

Sorry for this newbie question ;) , any help is greatly appreciated :D . I also tried looking around in this forum at internet connection related questions, but the problems people were having seem to be beyond the first setup stage. And so I made this new post =).

---

### Post by Bachstelze on 2006-11-30
Hi and welcome to Ubuntu

All you need to know about ndiswrapper is [here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) :)

---

### Post by towync on 2006-11-30
Hi, thx for the reply :), but I had been on that page before, and I guess my option is to try: 

6. Without Internet access
Without an Internet connection, you can still install ndiswrapper-utils from the Desktop CD. If you installed from that, the repository in which ndiswrapper-utils is found is on the CD, but not within the live session. You need to boot into your new Ubuntu installation and then reinsert the Desktop CD. You will be asked if you want to add the packages on the CD to your list of repositories. 

But when I popped in the (downloaded) kubuntu cd,  it never asked me whether I wanted to add packages, and when I browse the cd, I can't find ndiswrapper on it.

Anyways, think I gotta hit the pillows in a sec or two to catch some sleep (5am here lol) =). Thx, and see you guys tomorrow hehe.

---

