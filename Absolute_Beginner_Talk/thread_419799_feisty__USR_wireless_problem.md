---
title: "feisty / USR wireless problem"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by WHICKS on 2007-04-23
I'm a complete noob as it comes to linux.  I started using open source at work to cut down expenses and I am probably going to switch the whole office over at our next hardware upgrade.

I installed feisty on an older computer (AMD 1800, radeon ATI 9200 video, dual boot off a seperate hard drive), and I installed it with no problems (thanks to Falko for the ATI workaround).  I updated and installed while hard wired through an ethernet connection, but I have been having problems when I try to switch to wireless.  I have a USR 8054 router, and a USR pci wireless card.  The card is seen by the system software,but does not enable.  WEP and WPA are disabled on the router to make the process easier.  If I boot the system under XP, the card works fine.

Any suggestions?


The second question is in regards to beryl.  I installed it and have the cube and most effects working just fine.  The only thing I can't get to work is emerald.  I've looked at a few forums and tried a few things, but no luck.  Any suggestions for this one?


Thanks for looking, W.

---

### Post by lunchmeat5000 on 2007-04-23
I was having the same problem with my usr 5416 pci card.  What type of card is it?  Here's a link that might help.  It got mine working.
[http://ubuntuforums.org/showthread.php?t=96850&highlight=us+robotics+5416](http://ubuntuforums.org/showthread.php?t=96850&highlight=us+robotics+5416)
Can't help with beryl, I'm still pretty green at this stuff.

---

### Post by WHICKS on 2007-04-23
The router is an 8054 Turbo, and the PCI card is a Model: USR805416 Turbo PCI adapter.  In the meantime, I'll try your fix and see if that works.  Thanks.! W.

---

### Post by WHICKS on 2007-04-28
no luck so far

This is what I have so far:

warren@usr8054:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:C0:49:53:F9:2C   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=57/100  Signal level=41/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

warren@usr8054:~$ lsmod | grep acx
acx                    98564  0 
usbcore               134280  4 acx,ehci_hcd,uhci_hcd
warren@usr8054:~$ 


What should I try next.  Thanks in advance, W.

---

### Post by csnowman00 on 2007-08-29
I had the same problem. 

You need to upgrade the firmware for the router.  The router will work with XP and not Ubuntu or Vista.  It took me a week to figure it out.

Here is my post:
[http://ubuntuforums.org/showthread.php?t=534220&highlight=usr8054](http://ubuntuforums.org/showthread.php?t=534220&highlight=usr8054)

---

