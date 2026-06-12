---
title: "HP Laptop isn't connecting, wired or wireless."
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-07-25
Okay . . .I really need help with my nc8000 laptop. I've run through all the help articles I can think of and have found nothing pertaining to my issue. My wireless has turned itself off, and I can't turn it back on. On top of that, my ethernet has crapped out apparently, so I can't use that either. I do have a means of data transfer, however, and I was hoping that someone could lend some assistance. I require this computer for work purposes and need to have it connected. It may very well be that I need a new NIC, but I want to avoid that until necessary. Any help would be appreciated. Thanks.

---

### Post by shearn89 on 2007-07-25
is your card recognised at all? post output of "lspci" (run in terminal) here, and we'll have a look.

---

### Post by CheshireMac on 2007-07-25
~LOL~ Alright, I just found out that I can't view a saved text file from Ubuntu on a Windows machine, which is weird because I've done it several times before . . .okay, so the Network controller is an Intel 2200BG, which I knew. It does show up, along with everything else. I could type every detail out, but it would take me forever to do that at each step.

---

### Post by mlentink on 2007-07-25
Just cut and paste, that will save you the typing.

I have a HP Compaq nx7400 on which everything worked flawlessly out of the box.

---

### Post by CheshireMac on 2007-07-25
> **mlentink said:**
> Just cut and paste, that will save you the typing.
 
I have a HP Compaq nx7400 on which everything worked flawlessly out of the box.
I can't cut&paste from one computer to another . . .and there's no connection. This is getting really frustrating. I've tried all the manual power switches I can think of, and I've also tried turning the radio on (it is also off). None of this is working out well for me. 
Here is my eth1 config: 
radio off ESSID: off/any 
Mode: Managed  Channel: 0 Access Point: Not-Associated
Bit Rate:0 kb/s  Tx-Power: Off Sensitivity= 8/0
Retry limit: 7  RTS thr: off  Fragment thr: Off
Power management: ON (this is new, used to say off)
Link Quality: 0  Signal level: 0 Noise level: 0
Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
Tx excessive retries: 0  Invalid misc: 0  Missed beacon: 0

---

### Post by shearn89 on 2007-07-28
If thats the wireless card config (which it looks like), it should be under something like wlan0, not eth1.

---

### Post by CheshireMac on 2007-07-30
> **shearn89 said:**
> If thats the wireless card config (which it looks like), it should be under something like wlan0, not eth1.
Well, I only type what I see. Now, I've still found no way to reconnect, and it's been about a week now . . .I really am starting to become a little agitated with this machine. I'm working still with a Windows machine and it's not doing much in regards to helpfulness. 
If anyone has the time of day to help me work this issue, I'd be so happy and grateful. Thanks.

---

