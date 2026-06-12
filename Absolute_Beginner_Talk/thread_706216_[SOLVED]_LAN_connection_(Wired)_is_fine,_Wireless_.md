---
title: "[SOLVED] LAN connection (Wired) is fine, Wireless connection Screwed..."
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by linuxisfree on 2008-02-24
As the title suggests... I can only seem to access the web with my laptop using my wired lan connection, my wireless is SHOT! I just happened, though... It was working perfectly a week (3 days, more precisely) ago. Any ideas, suggestions? Anybody? What should i post that could be of help?

Thanks so much in advance!:)

PS: Nothing of note seemed to happened in between... it just literally stopped working.

---

### Post by superprash2003 on 2008-02-24
type iwconfig in your terminal and post the output here!!

---

### Post by linuxisfree on 2008-02-25
Hey, thanks for replying... anyway, here it is... I could be screwed here:(

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"WMonteblanco"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```A reinstall may be in order here... but i dunno, what do you think?

EDIT: Used the live CD, and what do you know... Wireless works there... hmmmm...
EDIT: I was able to solve it by reinstalling Ubuntu (Thank God i had partitioned my HDD!!!). I would still like your input as to any other means to have solved this issue... so that i don't have to keep reinstalling. Thanks!

---

