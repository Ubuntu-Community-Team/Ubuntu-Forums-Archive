---
title: "Help with WiFi and Screen resolution"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Damo1976 on 2007-03-19
Dear Ubuntu gurus,

I have just installed 6.10 on my laptop, and all seems OK, except...
1. I can't get the wireless working 
2. I can't increase the screen res beyond 800 x 600 - I want 1440 x 900.
3. I can't see any of my documents that are on the XP partition.

Can one or many of you offer some help please?

Damian

---

### Post by Hilding on 2007-03-19
'Lo there.
Please tell me the name/model of your laptop and I'll se what I can do.

/H++

---

### Post by loanrangie on 2007-03-19
When i installed Edgey onto my Toshiba Tecra M2 i was suprised that the wifi and everthing else worked straight away, this has given me confidence to attemp a full install - maybe.

---

### Post by muralishankarp on 2007-03-19
i'm working in a software company, here we use gentoo platform... 
in our application if u send mail to hotmail means its not getting delivered ..
if i send to other mails means it goes into spam..
can any one give a solution for it..

---

### Post by Damo1976 on 2007-03-19
Hi Loanrangie,

I have a Fujitsu Siemens Amilo Xi 1546.

It has 1GB Ram
Core Duo 2GHz
256mb graphics card (ati 1800 I think)
2 x 100GB hard drives.
1440 x 900 screen

I am also not sure whether the raid is now working properly.
I was thinking about making it one hard drive per OS...
Any advice on that would be cool too.  At the moment (on XP) they are just running as mirrors.

Thanks

Damian

---

### Post by Kobalt on 2007-03-19
1. For your resolution problems, open a Terminal and enter the following command line : 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
From there, select the resolutions you want as available for your monitor with the spacebar, then press Enter. Finally press Ctrl+Alt+Backspace to restart X, log back in and here you go...
2. Here is some doc on accessing your files on XP partitions : [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
3. We need more specific info, particularly the exact model of your card, to help you set up your wireless connection...

---

### Post by Damo1976 on 2007-03-19
hi,

The wifi card is the built in one:
Intel(R) PRO/Wireless 3945ABG

I also sometimes use a ZyXEL USB dongle (which has a better range for some reason).

Thanks

Damian

---

### Post by Damo1976 on 2007-03-19
Hi,

I followed Kobalt's post, and selected ati as graphic card type, then chose the correct res.
Then ctrl+alt+backspace.

That's where  all went wrong.
After what seemed like ages of hanging it re-started and then hung again.
Can't now get it to start up at all.
And now I'm back in XP again :( 

How do I fix this?

---

### Post by gameman12 on 2007-03-19
what happens when you reboot?

does grub load at all? and if so, what are your boot options?

---

### Post by natman on 2007-03-19
Hi,
I have a HP pavillion but with the exact same intel built in wireless, worked out of the box for me when i installed 6.10 ( ubunut 64 ). Kubunut would not detect it by itself it had to be told to do it, but ubunut worked fine. Not sure if thats any help.
Good Luck

---

### Post by Damo1976 on 2007-03-19
Well, glad to hear its not a fundamental problem with the card, but I still can't get the bleeder to work!!!!

---

