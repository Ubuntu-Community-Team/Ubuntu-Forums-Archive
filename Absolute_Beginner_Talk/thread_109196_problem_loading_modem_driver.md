---
title: "problem loading modem driver"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by APendragon on 2005-12-28
I've just loaded Ubuntu on an HP Pavilion laptop (ze2000) that dual-boots into Windows XP.  Ubuntu loaded OK, but I don't see my modem (AC97 internal) listed anywhere and can't use it (I'm on a dialup due to living too far from any broadband connections).  I've spent hours looking at instructions for various fixes; the least helpful advised me to pull something off the Internet.  This is a bit like asking a legless guy to try on a new pair of shoes.  My only Net access is via Windows XP, which I'm doing my best to get rid of by finding a Linux system I can work with.  I can download stuff via Windows but do not know how to get it into Ubunto, which I've placed in a separate partition on the hard drive.

Can someone refer me to a set of instructions that are actually clear and readable to someone new to Linux stuff?  "Just do it through ndiswrapper" or ndishwasher or whatnot doesn't help unless there are steps I can follow.  Same with the wireless:  it sees bcm4306 but won't load it.  Until I fix these I can't close the Windows.  Thanks!

---

### Post by towsonu2003 on 2005-12-28
First, two quick links from the wiki:

For ndiswrapper: [https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

For modem (winmodem): [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

These should be helpful.

For the modem, here is a very brief explanation: it will take a LONG time for you to understand and configure it. mine (hp pavilion zv5120us) took about 3-4 months and 6-7 different distros... 
a winmodem (your modem) is a piece of hardware that lacks some prime hardware pieces in it. So it outsources stuff to the CPU through software and/ or drivers. Very quickly (I'm a little sleepy :oops: ):
1. Read wiki (link above and in my signature)
2. go to linmodems.org
3. download, extract, and use scanmodem tool
4. read scanmodem's output (1stread.txt and modemdata.txt especially, but all others as well. 
5. either act upon that output or email linmodems.org emailing list ** *following the instructions** * within the scanmodem's output files...

As for the ndiswrapper, try to follow the wiki link above and preferably open a new thread (with title showing problem's nature ->ndiswrapper) if you have any troubles... 

I really hope this will help.

---

