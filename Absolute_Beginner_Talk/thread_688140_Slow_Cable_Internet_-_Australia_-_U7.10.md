---
title: "Slow Cable Internet - Australia - U7.10"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by m-k on 2008-02-05
Hi,
i am new to Ubuntu (and Linux) after years of using Win98 and then XP i decided to SUPPORT the linux "movement".

U7.10 installed and is running OK, but one issue is really bothering me. The cabl;e internet connection i have is much slower than my WinXP! I compared few websites and the time to open them and there is a definiate significance, U7.10 is much slower :(

both operating systems are installed on separate Seagate HDD's (removable drives)
my PC is 2.8Ghz, 2Gb RAM, 128Mb Graphics Card, i have cable modem Motorola SurfBoard connected via Ethernet cable. 

why is U7.10 internet slower than MS WinXP ?

please remember, i am an "end user" i have no knowledge of code entry or programing knowledge, so what i am after is an answer and help on how to resolve this issue.

i really want to use Linux (Ubuntu) but if this problem persists (i use internet frequently) i will have to return to Windows :(

thank you in advance.

---

### Post by R@inm@n on 2008-02-05
I'm in AU as well, and using Win XP and U 7-10 like you are. What browser are you using with U 7-10?

I use Firefox on both my operating systems, and both run about the same speed for internet use.

If you run Firefox, d'load "Fasterfox" from the Mozilla website and install it. Doing that helps make Firefox even faster.


   R.

---

### Post by m-k on 2008-02-05
Hi,

using Firefox 2.0 on both OS's...cable internet is with Bigpond...
U7.10 surfing speed definiately slower than XP  :(

downloading fasterfox now...also disabling all "eye candy" from OS will see how it goes Thank You :)

---

### Post by m-k on 2008-02-05
fasterfox downloaded...will test tomorrow later in the morning when i do most of my internet surfing.

also, have installed SWIFTWEASEL browser...if things improve i will use it instead of FireFox (since FF apparently is no longer made up of entirely free content - apparently someone decided to copyright the firefox graphics?!)

once again...thanks for your advice.
MK

---

### Post by bumanie on 2008-02-05
Hi, I'm from Aus too, I find no appreciable difference in speed between xp, 7.04 or 7.10. Unfortunately, I don't have solution off the top of my head. Be patient someone on the forum will come up with an answer at some point.

---

### Post by bumanie on 2008-02-05
Just looked up a 'digg' site re slow internet in gutsy. It talked about the ipv6 issue whereby you can disable ipv6 in firefox or blacklist it in modprobe.d
I have advised many to try one of these in the past, but that was when they could not get any connection at all - 90% of the time this fixed the problem. I was not aware that it was a problem with slowing the internet connection. If you wish to try the ipv6 solution, post back and I will give you the instructions. As I said, I know it often works for no internet connection. I cannot say whether it will fix your problem or not. If it doesn't help, the changes can be reversed. Blacklisting ipv6 was the only way I could get internet connection with 7.10.

---

### Post by Mahyar on 2008-02-05
Hang in there.

When I switched from XP to Dapper, I found no difference at all, so I'd say there's a configuration problem on your box.

I have iPrimus ADSL2 on the east coast.

---

### Post by gandaran on 2008-02-05
firefox is shipped in ubuntu to work with dial-up connections, if your Internet is broadband you can speed up firefox by just tweaking three settings
clear firefox navigator bar and digit » about:config «
change the following

http.pipelining (to) true
http.proxy.pipelining (to) true
http.pipelining.maxrequests (to a number like) 20    

gandaran

---

