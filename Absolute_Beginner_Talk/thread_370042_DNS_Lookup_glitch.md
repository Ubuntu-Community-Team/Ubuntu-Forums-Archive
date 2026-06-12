---
title: "DNS Lookup glitch"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by silkstone on 2007-02-25
I'm getting used to Ubuntu but still towards the bottom of the learning curve.

I'm having intermittent problems with the web browser stalling on 'Looking up <URL>'. Sometimes it will get there after a few seconds, but often it comes up with a 'Server cannot be found' error. This doesn't happen all the time - it seems a matter of luck whether it gets straight in or stalls.

I'm running the latest Edgy Eft - installed about a week ago. The problem happens with both Firefox and Opera (I installed Opera just to see if it made any difference).

After searching the posts here, I edited the 'disable IPv6' line using about:config in Firefox, so it now reads 'True'. I also edited the /etc/modprobe.d/aliases file so the line alias net-pf-10 ipv6 now has off instead of ipv6.

I think that has improved the performance, but hasn't removed the glitches altogether.

Any suggestions? TIA. :)

---

### Post by n8bounds on 2007-02-25
Sounds like you've already done some searching/reading.  Are you dual booting?  Does the other OS have the same problem?  Does the symptom persist from the live cd also?  Try these maybe:

[http://ubuntuforums.org/showthread.php?t=368896](http://ubuntuforums.org/showthread.php?t=368896)

[http://ubuntuforums.org/showthread.php?t=369907](http://ubuntuforums.org/showthread.php?t=369907)

[http://ubuntuforums.org/showthread.php?t=359503](http://ubuntuforums.org/showthread.php?t=359503)

I like opendns, use them if you can.

208.67.222.222
208.67.220.220

---

### Post by r4ik on 2007-02-25
Manually edit /etc/dhcp3/dhclient.conf and change the PREPEND line to something like this:
Code:
prepend domain-name-servers 123.45.67.89, 345.67.89.10;

Note the comma and space between multiple dns addresses and the semicolon at the end. Use real dns addresses of course.

---

### Post by silkstone on 2007-02-25
Many thanks. I'll follow that up. The problem is only with Firefox/Opera on Ubuntu. It's dual boot and FF on Win XP is OK.

---

### Post by r4ik on 2007-02-25
if you are interested in the whole thing,

[http://forums.debian.net/viewtopic.php?p=44352#44352](http://forums.debian.net/viewtopic.php?p=44352#44352)

---

### Post by silkstone on 2007-02-25
I'm interested and, again, many thanks. I wonder if it would be better if this could be resolved in the default installation. I'm moderately computer-literate and also persistent, but I'm sure that many people who try Ubuntu would be put off by something like this. ;)

---

