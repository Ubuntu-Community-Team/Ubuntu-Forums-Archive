---
title: "Advice on MythTV tv card setup"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Andrew Garn on 2007-08-28
I have an old PCI WinTV Card and a WinTV Nova-S USB external tv tuner.

Here was the website i used to install MythTV: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

I want to make one of them/both work with MythTV and would like practical advice on how to install the cards.

I know ubuntu has installed the Nova card as typing "grep -i dvb /var/log/messages" in the terminal yielded these results:

andrew@andrew-desktop:~$ grep -i dvb /var/log/messages
Aug 28 22:14:53 andrew-desktop kernel: [  951.005356] DVB: registering new adapter (Technotrend/Hauppauge Nova-USB).
Aug 28 22:14:53 andrew-desktop kernel: [  951.009355] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
andrew@andrew-desktop:~$ 

So based on those cards can someone explain to me how to install them in MythTV, as i've played around in capture card settings and couldnt get anything to work with channel search.

---

### Post by nonewmsgs on 2007-09-18
i honestly dont know much about it but i have read that knoppmythtv is easier to set up.  i would ask in the #mythtv irc room in freenode for more specific questions.

---

