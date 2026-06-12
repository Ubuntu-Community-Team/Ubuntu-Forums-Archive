---
title: "Hardware Support Issue with Edgy"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by CJShiami on 2006-11-07
Just installed Edgy today, upon recommendation from a friend and having had a chance to tinker with it.  I Purchased a new computer recently and figured that it would be a good opportunity to try ubuntu.

The install itself went find.  I can enter, access and use Ubuntu in a basic sense.

The problem is that Ubuntu does not recognize the drivers for the onboard components for my motherboard.  I am running:

ASRock AM2NF6G-VSTA
Network Chipset:  Realtek PHY TRL8201CL
Sound: Realtek ALC888 7.1 channel audio codec

Both the sound and network cards are currently unrecognized.  Since the network card is down, I cannot download in drivers while in Ubuntu, I have to obtain them while in windows and port them over to ubuntu by some means.  However, that shouldn't be too tough, I'd imagine. 

What I need to know is if there is somewhere I can obtain drivers for these devices that will work with Ubuntu, and I kinda need an idiots guide to getting them into the system.

Unfortunately, my experience with Ubuntu and linux in general has been limited to roughtly the last two hours I've spent muttering and cursing after install.

Any help would be appreciated.

---

### Post by ReaderRat on 2006-11-07
Realtek:  High Definition Drivers:
**[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs)**

---

### Post by CJShiami on 2006-11-07
thanks for the links to the audio driver I'll need.

That still leaves me with a few issues that are driving me batty.

A) That I can't figure out how to get that driver operational within Ubuntu

B) That the network card isn't operational, and the drivers for it are not included in the main realtek package.

C) that the utility in Ubuntu that is apparently supposed to detect my hardware settings (under Device Manager in the GUI) freezes up when it reaches the point where it is supposed to detect my network card.


At this point I'm really just too frustrated to continue working on this.  Feel free to post anything you think will be helpful, but I'm going to give up for the evening.  At least I went for a dual boot so I can stick to windows if need be.  

Any pointers? Feel free to leave them here for me.

---

### Post by COL on 2006-11-20
Hi,

I just got a system with the RTL8201CL ethernet interface and the Realtek ALC888 audio.  I was very surprised that they weren't recognized under Ubuntu (or most other distros as well, as far as I could tell)...

What to do?  I think quite a few people are going to have this problem.  I have the ASRock AM2NF6G-VSTA motherboard, and I think it might be a popular choice.

Anyhow, like the messages above...help!!!

---

### Post by pjman on 2006-12-20
I tried installing both Dapper and Edgy on a new machine that has a ASRock AM2NF6G mother board. Does anyone have any ideas on how to get the LAN working for it? Anyone?

---

### Post by rtomek on 2007-01-07
I just bought the ASRock-VSTA motherboard, and when I built my kernel I had to add VIA Rhine network support under the drivers for 10/100 adapters and it worked great.  You might have to rebuild or upgrade your kernel to one with the 'VIA Rhine' network driver support, unless you can find a module to install.  I just rebuilt the kernel, it only took about 3 minutes.  I am currently installing gentoo and don't know about the sound card yet, maybe later today I will figure something out.

---

### Post by Ocxic on 2007-01-07
try installing the linux-restircted-modules package in synaptic if it's not installed already

---

### Post by maryjanua on 2007-09-19
did u ever get this fixed ? i have an asrock board which needs that driver and i got it solved
check this thread out around page 11 may help
[http://ubuntuforums.org/showthread.php?t=550753](http://ubuntuforums.org/showthread.php?t=550753)
regards mj

---

