---
title: "T-Mobile Sony-Ericsson GC89"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by ceg on 2007-01-17
I need a driver so I can connect to the internet through a GC89 air card on the T-Mobile network. Otherwise I have to go back to XP to connect. Help!

---

### Post by aws910 on 2007-12-14
This page made mine work within minutes:

[http://erikstambaugh.com/gprshowto.html](http://erikstambaugh.com/gprshowto.html)

At first it didn't work, but when I changed internet2.voicestream.com to wap.voicestream.com it worked like a charm.  Using it to post this.  PM me if you need more help.

---

### Post by linxuser14 on 2008-04-16
First of I'm replying from my windows. I have dual-boot set up with kubuntu 6.06. Just got this gc89 card couple of weeks ago. I originally couldn't get kppp(gui access to pppd)  to access gc89 till I set the modem speed to 57600. Otherwise it communicated jiberish to gc89 and no response. Then it did ATZ to gc89 with response of ERROR. After reading Squinky's how to I copy/pasted his /etc/ppp/peers/tmobile , his 2 gc89chat files to (I think it was in /etc/ppp/peers could've been /etc/ppp...I'm not in kubuntu now)  Ran pppd call tmobile and it didn't connect. But after that kppp can communicate with gc89. Setting dialing # to *99***1# with username ' ' and password ' ' enabled it to connect. But then it would hang up/reconnect every 2 minutes. Then...

        -next is copy/paste from my kate-

In /etc/ppp/options I commented out lcp-echo-failure 4 and removed the comment-out (#) from the line -vj (something about jacobson compression) I think it disabled it but I did use (#) before lcp-echo-failure 4 to disable it. Anyway kppp no longer hangs up and reconnects every 2 minutes. there was a line saying lcp-echo-interval 30 that I left unchanged. i guess that explains the 2 minute hang up/reconnect time. Anyway it works fine. Just speed is maybe not at optimal. speedtest shows 40 kb/s using LAX and Mpls,Mn servers. 50 kb/s doing Scottsdale.AZ server. But it works. Anyone know specifically what files contain settings I've stumbled on that make it work, request and I'll be glad to post em. I'm not sure if my other problem where kppp couldn't communicate with gc89 till after I do a pppd call tmobile is still an issue till I halt and try again another day. But yeah! Internet in kubuntu. p.s. I'm running 6.06 I think. I'm going to boot to kubuntu and see if it works now.

---

### Post by linxuser14 on 2008-04-16
O.K. I switched to kubuntu. It now connected using pppd call tmobile. That link to Squinky's how to is the same as AWS910 shows in his reply ( [http://erikstambaugh.com/gprshowto.html](http://erikstambaugh.com/gprshowto.html) ) . Now I have to figure how to hang up from pppd. Guess I'll browse around and find the info. Otherwise I can go into kppp and in configuration, configure modem and go to its terminal window and try +++ and ATH or ATH0. Maybe that'll get me disconnected. Had the same problem using kppp first where the gc89 responds to ATZ with ERROR. So tried pppd call tmobile. Thats how I'm here. Hope this helps. Good luck.

---

### Post by linxuser14 on 2008-04-16
O.K. I'm back. Whew. In order for me to hang up pppd I found the command to use was poff tmobile. Now I'm connected using kppp (gui) . I like it better cause it leaves a communication icon on my task bar that lights up when its communicating. I know the progress bar on the browser shows somethings happening and status line, but I like the little lights indicator. O.K thats it. Still have to start communication with gc89 using pppd call tmobile. Then disconnect using poff tmobile. Then kppp works.

---

### Post by Arch2 on 2008-04-17
I think you need to put AT+CFUN=1 in your Initialization string.
This command turns on the radio on, then it takes a little while before the modem is ready for another command. So, the first time you try to connect in KPPP it will probably fail. Wait a few seconds and try again then it should connect. 

Disconnecting does not turn the radio off. To do this you need to send it AT+CFUN=0.
I use gtkterm to manually send commands to the modem. Kterm may work better in KDE.

This post should help.
[http://ubuntuforums.org/showthread.php?t=374314](http://ubuntuforums.org/showthread.php?t=374314)

---

