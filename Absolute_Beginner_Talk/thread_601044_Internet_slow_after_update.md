---
title: "Internet slow after update"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-11-02
Hi,

my internet became slow after updating my ubuntu. It is slow only when it is trying connect to the page, after connecting everything downloads properly. The same to downloads, it is slow to start downloading, but when it starts it downloads as before.

The same happened to my flat mate, He also uses ubuntu, and he came to ask me if my internet was slow, but at the time I hadnt updated my ubuntu. But after, I got the same problem as he.

Internet connection in windows is normal, so I guess the update did this problem. I`m sure actually.

I dont know if it has something to do with /etc/hosts, but it is like this now:

> 127.0.0.1       localhost
127.0.1.1       bruno.krebs     bruno

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Maybe it is missing the address of the wireless modem?

Please, help.

Thanks
Bruno

---

### Post by frank002 on 2007-11-02
I had the same problem and after I disabled IPv6, it resolved the issue. Here is how to do it:
To fully disable Ipv6:
gksudo gedit /etc/modprobe.d/aliases
Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
By the way, This all started after I upgraded to Gutsy from Feisty. Let me know if this helps. Thanks.
__________________

---

### Post by brunoskrebs on 2007-11-02
Oh yeah,

it worked perfectly. Thank you very much.

By the way, can someone give me a good explanation why does this happens? And am I not losing anything turning of the ipv6??

Thanks again...

Bruno

---

### Post by destineal on 2007-11-03
speed tests for me indicate 799Kb/s downstream in Linux vs. 6000Kb/s in Windows using same wireless card. IvP6 off didn't work 4 me

---

### Post by brunoskrebs on 2007-11-03
yeah, u dont have the same problem as me. Because, like I said before, my speed was ok, after connecting to the host. The problem was in the connection. For example, when I tried to download something, it took ot much time to start, but after starting the speed was as good as before.

By the way, if you download something, your download rate on linux is worse then on windows?

---

### Post by drizkill on 2007-11-03
> **frank002 said:**
> I had the same problem and after I disabled IPv6, it resolved the issue. Here is how to do it:
To fully disable Ipv6:
gksudo gedit /etc/modprobe.d/aliases
Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
By the way, This all started after I upgraded to Gutsy from Feisty. Let me know if this helps. Thanks.

Registered just so I can say thanks! Edited the file, saved, and it worked like a charm! DL went from 950KB to 9450KB; you're a life saver :D

That was driving me nuts!

ps. the fix worked at first but stopped after a reboot. After doing a little more digging I found I needed to use a different line change to:   alias-pf-10 off ipv6

---

