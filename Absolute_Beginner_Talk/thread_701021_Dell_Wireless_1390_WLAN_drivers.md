---
title: "Dell Wireless 1390 WLAN drivers"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Szdfan on 2008-02-18
Hi,

I just installed Gutsy onto my Dell Inspiron 1521, so of course I have the 1390 WLAN Mini-Card.  My understanding from reading the forums, is that I will need the Broadcomm 43XXX drivers from Dell for this work.  I found the following [_[COLOR="Navy"]walk through[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Wireless+WLAN+1390") and it seems to me that this is what I am going to need.  

2 Questions --

1) What is Ndiswrapper?
2) The walk through obtains the drivers from the Dell website.  Unfortunately, the only internet access I currently have is a wireless connection.  I thought I may download the drivers via Vista, put them onto a thumb drive and install them from the drive in Ubuntu.  What is the command I need to type on the wget line in order to pull the driver of a thumb drive or desktop?

Thanks!

---

### Post by kryth on 2008-02-18
Ndiswarapper basicaly lets you use Windows Network card drivers in Ubuntu.
I've never used it. I tried but never could get it to work.
I used a wired connection to install the resticted drivers, then wireless worked fine on my dell 1520. Not much help i know. :(

---

### Post by kryth on 2008-02-18
2) What i would do is in Windows download the Dell Drivers for your card. Open the exe or unrar the exe, so you have a folder of inf's etc. Copy that to thumb. Then download the ndiswapper tarball, and save to thumb driver. REboot into ubuntu, then copy those files to your desktop or anywhere you want. Then you should be able to follow the Howto more or less.

---

