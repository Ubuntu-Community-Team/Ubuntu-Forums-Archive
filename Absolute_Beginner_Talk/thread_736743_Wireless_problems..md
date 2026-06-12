---
title: "Wireless problems."
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Jon11393 on 2008-03-26
I own an inspiron 6000 laptop and connecting to wireless networks via the nm-applet (0.6.5) has been fine until very recently. 

When I attempt to connect, or view wireless networks nothing appears. 

I'm _very_ new to Ubuntu (gusty) and was wondering if someone could help me solve this dilemma as I don't know how to connect to a wireless network any other way.

---

### Post by dsauxier on 2008-03-26
Try System->Administration->Network Tools.

If that gets things going, then don't bother reading any further.  But if that doesn't show anything... does your laptop have a button to enable/disable wireless?
Mine does, and everyonce in a while I'll accidentally bump it (annoying).

If neither of those suggestions help, can you go to a terminal and type ```
 sudo iwconfig
``` then post the results here?

---

### Post by Jon11393 on 2008-03-27
Thanks for the help! I can't copy-paste this so I'm going to type if (sorry if there are any mistakes):

lo                  no wireless extensions

eth0              no wireless extension

eth1               radio off ESSID:" "
                       Mode: Managed   Channel:0    Access point: Not-Associated
                       Bit Rate: 0 kb/s          Tx-Power=off          Sensitivity: 8/0
             
I think that's all thats important... I don't believe my laptop has a wireless on/off button.

---

### Post by Jon11393 on 2008-03-27
Upon inspection of the user manual I found there is a hotkey (ctrl-alt-shift-f2) that turns the wireless on/off... thanks for the help though! (I feel like an idiot)!

---

