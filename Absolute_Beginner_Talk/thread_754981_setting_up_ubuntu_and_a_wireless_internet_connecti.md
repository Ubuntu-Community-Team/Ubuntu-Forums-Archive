---
title: "setting up ubuntu and a wireless internet connection"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by irshman on 2008-04-14
hi

i'm a linux novice

I set up a dual boot with vista but was having a few issues connecting to the internet with my netgear wg111 v2 so removed it 

ubuntu 8.04 is out in 10 days and i intend to format my hard drive and get rid of vista altogether but i'm worried i'm not gonna be able to get online easily

i really don't want to spend days trying to set this up

i've been put off the idea by the mass of forum problems relating to this issue

i've got a spare PCI wireless card - should i install this - will it be any easier to get online??

thanks for the help

---

### Post by anewguy on 2008-04-14
The answer would be "depends".  It would depend on the chipset on the PCI adapter.  My suggestion would be to look through the forums for which chipsets/manufacturers people are having trouble with and stay away from them.  Instead, try searching the forums or the net for a list of "compatible" or "works with Linux" adapters.  It will take some searching, but that way you can be prepared for what you need to do and have the files and programs ready if you need to.  I know there are adapters that just work with Ubuntu - I have a Belkin Wireless G USB Network Adapter I got at WalMart for around $40 and it has just worked "out of the box" with Ubuntu Feisty and Gutsy.  Didn't have to install drivers at all.

:)

---

### Post by northern lights on 2008-04-14
Plug in the wireless card and check - it probably works under your current distro already. Do I understand you correctly - you'reposting from Windows and you've got no net under Linux? Can you activate all ethernet devices and post the outputs of ```
lshw -C network
``` and ```
route -n
```

---

