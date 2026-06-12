---
title: "Internet only works for some web sites"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-09-04
The internet can open pages like google and this forum but not debian's website, for example. On the whole though the internet seems really slow. Is this my settings that I'm unaware of or something else?

```
PING www.google.com (72.14.205.147) 56(84) bytes of data.
64 bytes from 72.14.205.147: icmp_seq=1 ttl=247 time=17.1 ms
64 bytes from 72.14.205.147: icmp_seq=2 ttl=247 time=18.3 ms
64 bytes from 72.14.205.147: icmp_seq=3 ttl=247 time=17.4 ms
64 bytes from 72.14.205.147: icmp_seq=4 ttl=247 time=16.6 ms
64 bytes from 72.14.205.147: icmp_seq=5 ttl=247 time=17.0 ms
64 bytes from 72.14.205.147: icmp_seq=6 ttl=247 time=36.4 ms
64 bytes from 72.14.205.147: icmp_seq=7 ttl=247 time=17.0 ms
64 bytes from 72.14.205.147: icmp_seq=8 ttl=247 time=19.3 ms
64 bytes from 72.14.205.147: icmp_seq=9 ttl=247 time=17.7 ms
64 bytes from 72.14.205.147: icmp_seq=10 ttl=247 time=17.4 ms
64 bytes from 72.14.205.147: icmp_seq=11 ttl=247 time=18.2 ms

--- www.google.com ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 150586ms
rtt min/avg/max/mdev = 16.648/19.360/36.471/5.460 ms

```

```
ping: unknown host [www.debian.org](www.debian.org)
```

---

### Post by Niklas Schröder on 2007-09-04
which browser are you using?

---

### Post by arijarot on 2007-09-04
> **Niklas Schröder said:**
> which browser are you using?

I'm using iceweasel (firefox) v 2.0.0.6 and I should note that the internet worked perfectly before and now it is working normally again... but, I'm still curious as to why it starting to work selectively with certain sites and not others all of a sudden...

---

### Post by Niklas Schröder on 2007-09-04
lol.  iceweasel?  never heard that one.  :p  that's weird.  the only problems i've had with it is the often strange crashes when closing a flash-based site...

---

### Post by sbassett on 2007-09-04
sounds like a dns issue. try pinging 194.109.137.218. If that works change your dns to the settings listed at OpenDNS.com

---

### Post by Josh1 on 2007-09-04
Could be an MTU issue, I know my ISP required me to change my MTU from 1500 to 1200 when I couldn't access websites.. worked perfectly after that.

---

### Post by arijarot on 2007-09-04
> **Niklas Schröder said:**
> lol.  iceweasel?  never heard that one.  :p  that's weird.  the only problems i've had with it is the often strange crashes when closing a flash-based sight...

Iceweasal is debian's name for firefox. I think it has something to do with there licence or name restriction or something...

I guess this will just remain a mystery for now:)

---

### Post by Niklas Schröder on 2007-09-04
oh.  :p  i still like it a little better than firefox.  cause an iceweasel is an ermine!  :D

EDIT: sorry for the randomness and lack of help.  ;)

---

### Post by arijarot on 2007-09-04
> **Josh1 said:**
> Could be an MTU issue, I know my ISP required me to change my MTU from 1500 to 1200 when I couldn't access websites.. worked perfectly after that.

Since I don't know what my domain name server is or what MTU means, I have a question before I change these things.. if these things were the problem, why would the internet work before and after this strange internet behavior episode?

---

### Post by dpar on 2007-09-04
I was just going to suggest what sbassett said.:)

To find out the ip address of a website, open a terminal and type

```
dig www.thedomainname.com
```
if the name ends in org or net or whatever, replace the com with that.

---

### Post by Josh1 on 2007-09-04
> **arijarot said:**
> Since I don't know what my domain name server is or what MTU means, I have a question before I change these things.. if these things were the problem, why would the internet work before and after this strange internet behavior episode?

Didn't know it didn't work before. Sorry.

---

### Post by arijarot on 2007-09-04
> **Josh1 said:**
> Didn't know it didn't work before. Sorry.

No problem:) glad to see the level of interest in helping someone out is so good though!

---

### Post by gautada on 2007-09-04
This is very similar to my [post]("http://ubuntuforums.org/showthread.php?t=541299").  Word that I have been getting is that this is a firefox issue.  I have had to install opera

---

### Post by sbassett on 2007-09-04
> **arijarot said:**
> I'm using iceweasel (firefox) v 2.0.0.6 and I should note that the internet worked perfectly before and now it is working normally again... but, I'm still curious as to why it starting to work selectively with certain sites and not others all of a sudden...

This could very well be an ISP issue. It has happened to me from time to time, and a few of my friends all to often, but they use a cable provider that starts with C and rhymes with Omcast.

---

### Post by arijarot on 2007-09-04
> **gautada said:**
> This is very similar to my [post]("http://ubuntuforums.org/showthread.php?t=541299").  Word that I have been getting is that this is a firefox issue.  I have had to install opera

very interesting ... maybe I'll give epiphany a shot since it's already installed... thanks :)

---

### Post by arijarot on 2007-09-04
> **sbassett said:**
> This could very well be an ISP issue. It has happened to me from time to time, and a few of my friends all to often, but they use a cable provider that starts with C and rhymes with Omcast.

I thought of this too since all other things were held constant... but this is out of my hands... so...

---

### Post by sbassett on 2007-09-04
> **arijarot said:**
> I thought of this too since all other things were held constant... but this is out of my hands... so...

If you feel like giving OpenDns a shot, it even has instructions for Ubuntu, kudos to them for that.

---

### Post by arijarot on 2007-09-04
> **sbassett said:**
> If you feel like giving OpenDns a shot, it even has instructions for Ubuntu, kudos to them for that.

Thank you for the suggestion and pointing out the ubuntu guide. I don't think I want to play around with these settings as things are working now; but, if things go weird again, I'm happy to know that I have this as an option for troubleshooting. cheers :)

---

### Post by gautada on 2007-09-04
> very interesting ... maybe I'll give epiphany a shot since it's already installed... thanks

For this purpose epiphany is firefox...  if you can ping the ip address try opera.

---

### Post by arijarot on 2007-09-04
> **gautada said:**
> For this purpose epiphany is firefox...  if you can ping the ip address try opera.

ok:) I'll look into opera. thanks:popcorn:

---

### Post by arijarot on 2007-09-04
Is opera any good?

---

### Post by gautada on 2007-09-06
I am not a regular Opera user but to slove my problem it worked.  It is small compact and has lots of features.  Proponents of Opera claim (rightfully I believe) that most of the great features that have emerged into browsers lately are derived from Opera (tabbed browsing, etc).  As I said I have it installed for the pages that do not render correctly in FireFox.  My main browsing is still in FireFox.

---

### Post by arijarot on 2007-09-06
> **gautada said:**
> I am not a regular Opera user but to slove my problem it worked.  It is small compact and has lots of features.  Proponents of Opera claim (rightfully I believe) that most of the great features that have emerged into browsers lately are derived from Opera (tabbed browsing, etc).  As I said I have it installed for the pages that do not render correctly in FireFox.  My main browsing is still in FireFox.

OK. thanks for the info. cheers.

---

