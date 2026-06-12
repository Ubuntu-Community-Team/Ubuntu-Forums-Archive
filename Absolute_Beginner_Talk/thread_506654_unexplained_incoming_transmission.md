---
title: "unexplained incoming transmission"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by jrev on 2007-07-22
Hi all,

I am on Dapper 6.06 and I can see sometimes (with gkrellm) incoming transmission without:confused: any explanation.
There is no application busy and no browser in activity.

How can I find out the cause of this problem ?

Thanks in advance

---

### Post by p_quarles on 2007-07-22
It might be the repositories giving your system up-to-date info about security updates. 

Aside from that, do you have any internet services running? SSH? Apache? Anything like that? 

If yes, you might want to investigate further. If not, though, you're pretty safe.

---

### Post by jrev on 2007-07-22
I might be pretty safe but this incoming transmission impair the speed of my browser when I am on the Net

I wish I could find out which program is on to that transmission.

"Aside from that, do you have any internet services running? SSH? Apache? Anything like that?
"

I never used  apache or SSH on my machine ...

I got a local lan on three machines all ubuntu

---

### Post by p_quarles on 2007-07-22
Can you find out the IP address that's connecting with you? If so, you can try resolving that to a domain name. There are numerous ways of doing this, one being this web site:
[http://www.webyield.net/domainquery.html](http://www.webyield.net/domainquery.html)

There's also a good network activity monitor called Etherape, and you might be interested in running that to get a clearer picture of what's going on.

---

### Post by weblordpepe on 2007-07-22
Yeah or Wireshark.
Packet sniffers / network protocol analysers are beautiful things.

---

### Post by p_quarles on 2007-07-22
I guess I should add, too, that if you *don't *already know the incoming IP address, Etherape and Wireshark can both help you get it.

Also, how are you connecting to the internet? If it's wired, what kind of connection? Does your modem/router/gateway have a built-in firewall? If it's wireless, is it your connection, or a free connection?

---

### Post by jrev on 2007-07-22
> **p_quarles said:**
> Can you find out the IP address that's connecting with you? If so, you can try resolving that to a domain name. There are numerous ways of doing this, one being this web site:
[http://www.webyield.net/domainquery.html](http://www.webyield.net/domainquery.html)

There's also a good network activity monitor called Etherape, and you might be interested in running that to get a clearer picture of what's going on.

Excellent idea. I am going to try it out 
Thanks for this bright idea ...

---

### Post by jrev on 2007-07-22
> **p_quarles said:**
> I guess I should add, too, that if you *don't *already know the incoming IP address, Etherape and Wireshark can both help you get it.

Also, how are you connecting to the internet? If it's wired, what kind of connection? Does your modem/router/gateway have a built-in firewall? If it's wireless, is it your connection, or a free connection?

Very good question ...

I am connected through an external modem RTC low speed 56K to an internet provider called Alice and I got firestarter watching my connecting PC 

All wired, no Wifi

---

### Post by p_quarles on 2007-07-22
> **jrev said:**
> Very good question ...

I am connected through an external modem RTC low speed 56K to an internet provider called Alice and I got firestarter watching my connecting PC 

All wired, no Wifi
Okay, I've never seen a dial-up modem with any kind of hardware firewall, so that could be an issue. 

It's a common mistake to believe that running firestarter gives you a firewall. In fact, it's only a GUI configuration utility *for *the firewall. It's actually a bad idea to run it |EDIT: should be "to keep it running"|, since it has the ability to open ports and runs itself as root. Close that, and use either Etherape or Wireshark to watch your system.

---

### Post by jrev on 2007-07-22
> **p_quarles said:**
> Okay, I've never seen a dial-up modem with any kind of hardware firewall, so that could be an issue. 

It's a common mistake to believe that running firestarter gives you a firewall. In fact, it's only a GUI configuration utility *for *the firewall. It's actually a bad idea to run it |EDIT: should be "to keep it running"|, since it has the ability to open ports and runs itself as root. Close that, and use either Etherape or Wireshark to watch your system.

I am ready to use Etherape instead of firestarter if you think it can be of some use.
I 'll try to install it 
Bye for now, dinner is ready ...:)

---

### Post by weblordpepe on 2007-07-22
Whats for dinner? I'm starved.

---

### Post by jrev on 2007-07-22
> **weblordpepe said:**
> Whats for dinner? I'm starved.

Delicious french speciality : magret de canard. do you ever heard of it ?

---

### Post by jrev on 2007-07-22
Well, Etherape doesn't work with ppp0  ...

Will probably be the same with Wireshark  :(

I didn't know the update manager could download the new lists of packages without any permission from user or admin !

---

### Post by weblordpepe on 2007-07-23
To use wireshark you gotta be root user.
And never heard of magret de canard. Although it sounds like a cooked dog.

---

### Post by Mornedhel on 2007-07-23
It's duck.

Magret de canard is indeed delicious.

---

### Post by weblordpepe on 2007-07-23
Quack!

---

### Post by jrev on 2007-08-05
To add some precisions, the trouble starts when I open firefox to connect to my favourite forum.

I can stop this incoming transmission only by switching off the Internet connection.
When I put it back, everything is fine until I open again firefox which undoubtedly starts the trouble.

How do you explain that ?

---

### Post by _duncan_ on 2007-08-06
Is it possible firefox is trying to update some of the installed plug-ins?

I'm using feisty 7.04. I noticed that one of the recent feisty updates included firefox. When i launched firefox after updating the system, the first thing it did was to check if all my firefox plug-ins were up-to-date.

BTW, I'm also on dial-up, so I know how it feels if another program is sharing my precious 56k bandwidth while browsing. :)

---

### Post by jrev on 2007-08-13
All applications are shut down including firefox 
so i don't know how to locate the fault 
Whether it's a transmission asked from the PC itself or if there is somebody sending from outside.

My firewall is OK tested on the net and i moved this PC from main computer/router to a lan PC and the fault is still there ... :(
If I cannot find the fault I wlll install feisty instead of Dapper ...

---

### Post by weblordpepe on 2007-08-15
connect another computer to your LAN & put a packet sniffer on that computer. hmm i need to pick my nose.

..hmm..found a booger. oh yess, dried blood.

hmm.. crunchy.

---

### Post by jrev on 2007-09-17
**I changed from Dapper to feisty on that computer and the fault is still there ...**

---

