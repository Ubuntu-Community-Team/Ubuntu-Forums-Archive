---
title: "Trouble connecting to ISP"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Madmat on 2006-07-21
I am using Kubuntu 6.06 and have an external serial modem which was recommended by a forum user.
I have configured it in KPPP and dialed out to my ISP but it disconnects as soon as the verification process starts and gives me the error:

Jun 25 16:26:03 ubuntu pppd[7600]: The remote system is required to authenticate itself
Jun 25 16:26:03 ubuntu pppd[7600]: but I couldn't find any suitable secret (password) for it to use to do so.
Jun 25 16:26:03 ubuntu pppd[7600]: (None of the available passwords would let it use an IP address.)

wvdialconf finds the modem and I can query it in KPPP, however, ifconfig does not see it and it does not show up in the Network Settings (only eth0 and lo show).
Is my modem supposed to show up in Network settings? Or, do I have another problem?

---

### Post by zxee on 2006-07-21
Did you try sudo pppconfig in a shell? That will set up the modem and create needed files in /etc/ppp. Make sure your user is allowed to dial out-access the modem (although it sounds like you have that) I usually add myself to dial out through the advanced section in pppconfig. Also check out the options file in /etc/ppp if you continue to have problems. Hope that helps.

---

### Post by Matchless on 2006-07-22
If you are using kppp you should uncomment the line #noauth to become noauth in /etc/ppp/peers/kppp-options

---

### Post by Madmat on 2006-07-22
zxee, thank you.  It took 5 minutes and now I am replying to the forum from my Dapper box.  I guess the GUI version was missing something.

Matchless , thank you for your input. I have not tried this yet.

---

