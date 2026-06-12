---
title: "Help! Install stuck on&quot; scanning the mirror&quot; 82%"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Tony3286 on 2007-08-04
I was doing a dual boot install on my Windows XP computer. Everything was going well - did the 2 partitions , one swap other for the program. Looked fine until the "Installing system" box turned into
"Scanning the Mirror" and its been stuck on 82% for the last 20 minutes.
I can click on Applications, Systems, etc and the drop downs appear, but the install is stuck on that 82% for scanning the mirror - Help! Its Panic time ! ! ! !

Tony

---

### Post by Tony3286 on 2007-08-04
I also had read previous threads and disconnected my internet with no help - still stuck - using my wifes computer to get HELP

---

### Post by benx009 on 2007-08-04
could you post a screenshot of your problem?  (you can still use the live cd to that, right?)

---

### Post by Tony3286 on 2007-08-04
FINALLY after another 10 minutes after I disconnected by computer from my Linksys router the install continued. Now two problems:

  1. When my system tries to boot into Ubuntu I get a red message
"Signal over Range" and it keeps walking down to the bottom portion of my screen and then Ubuntu desktop appears.

2. For some reason, I open Firefox, it comes up, however  will not go to Yahoo, etc. The ONLY thing that works is the GOOGLE search. I can type anything in there, it appears, but when you click on any link , it wont connect.

---

### Post by anagor on 2007-08-04
If you can, enter into your router and find out what are the DNS servers it uses, or you can find it on your ISP's web site.
Then enter them using NetworkManager in it's connection properties, in the Domain Name System tab.

I've experienced the same problem myself, it happens with some routers, but not all, for some unknown reason (for me at least), that the router can't forward properly a DNS request from some, again not all programs, running under Linux.

As I said, just enter the DNS addresses instead of the one that is there, which will be the routers address.
It should take care of you problem.

---

### Post by Tony3286 on 2007-08-04
Your FANTASTIC - I just added my routers DNS sever # and works perfectly! Can I remove the previous DNS numbers that were there prior to my DNS?

---

### Post by garferi on 2007-10-18
> **Tony3286 said:**
> Your FANTASTIC - I just added my routers DNS sever # and works perfectly! Can I remove the previous DNS numbers that were there prior to my DNS?

Hi!
Can you tell me step by step, how did you resolve this problem?
I'm not too good at the DNS servers.

Thanks!

---

### Post by Tony3286 on 2007-10-18
I'm at work, so quickly - each router should have an IP address you use to get into the routers setup - something like 129.1.1.0    - you would type that in your browser in the address field ( where you normally type [www.etc.com)and](www.etc.com)and) you should get into the router  where you have to enter a user name and password - Once you enter those two entries and you actually get into the configuration options for the router, check what you have in there for the DSN #'s -  add those numbers in Ubuntu as explained above and you should be all set

---

### Post by lazka on 2007-10-18
[http://ubuntuforums.org/showthread.php?t=579920](http://ubuntuforums.org/showthread.php?t=579920)

---

### Post by mustardman on 2007-10-18
I am having EXACTLY the same problem.  7.10 32bit desktop version.  In my case it is a fresh install from scratch.  Hard drive wiped clean and formatted as part of default install from live cd.  I can run Firefox and browse internet no problem so DNS is definitely working fine.  At least with Firefox.  Connection information shows my router IP has been set up as primary DNS.  Disconnecting network cable as per other link worked for me.  I hope they add a timeout to this part of the setup.

---

### Post by xc3RnbFO8P on 2007-10-18
> **mustardman said:**
> I am having EXACTLY the same problem.  7.10 32bit desktop version.  In my case it is a fresh install from scratch.  Hard drive wiped clean and formatted as part of default install from live cd.  I can run Firefox and browse internet no problem so DNS is definitely working fine.  At least with Firefox.

Never had this problem doing EXACTLY the same thing with 7.04 32 and 64bit

It just heavy traffic on the server.

---

### Post by Wuhulf on 2007-10-18
I got stuck at "scanning the mirror" 82% of installing ubuntu 7.10. I think my problem is that i'm behind a proxy-server. My work-around was to pull out the net cable, and the installation continued.

---

### Post by Lucky A on 2007-10-18
Take it easy, guys, it ain't no bug, just a whole bunch of people rushing and overwhelming the mirrors at the same time. I, for one, has been at "ready, set...", waiting for the "go!" for a couple of weeks now!

Anyway, everything is working - just have a little patience. Takes ~ 15 min to creep past the "82%" points. Again, the mirrors are slow to respond. Wanna do it quickly - unplug your network cable. Wanna do it right - be patient and trust the mighty tux! Meanwhile, start the System Monitor and watch  you net card send beeps into the sea, and whales (mirrors) respond occasionally :) It's like watching the fire - passes the time and can't get enough of it! ....Ok! Mine is done! See you in ubuland!

---

### Post by coront on 2007-10-19
what happens if I just unplugged the cable?? :( what should I do instead?

---

### Post by Zenchess on 2007-10-19
I waited, it took about 10-15 minutes like the earlier poster said and then it continued.  Wish I would have read this thread and disconnected the cable.  

That part wasn't nearly as bad as the magic I had to pull off to boot in vesa mode.  Looking forward (ha) to getting fglrx drivers to work!  LVDSBiosNativeMode here I come!

---

### Post by rootie on 2007-10-19
Wow, the servers must really be under heavy fire... I feel like I've been stuck at 82% for ~20 minutes now...

Finally! On to 83% :D

---

### Post by Inkpot on 2007-10-19
This is just overcrowded servers. I had the same issue and unplugged my internet connection when it hit the "82% Freeze". Installation continued once I did this and after it was finished I just waited awhile before trying to update.

It's just crowded servers here folks, nothing to worry about. Be patient.

---

### Post by keisatsu on 2007-10-19
I thought I was having a problem here too, but I just waited a while and Ubuntu eventually continued with the install (not sure how long I waited, but it was a long time).

Patience is the key...

---

### Post by guhpraset on 2007-10-26
Me too have the same problem, the weird 82%.

After more than 8 hour, i found this thread. I wish i found many hours before :((

Now i will unplug the cable... see you on the next step...

---

### Post by Jim-BobH on 2007-12-18
I don't believe it is "just busy servers". I waited over an hour, watching the traffic indicator LED on that port of my LAN switch, and it seemed to be doing essentially nothing. Then, as soon as I did the following, it immediately proceeded and completed in a couple minutes:

Choose System >> Administration >> Network >> WiredConnection >> Properties (this shows eth0 with roaming mode (whatever that means) enabled).

Uncheck "Enable roaming mode".

Choose the following (this is for my LAN, which has a BEFSX41 gateway router with LAN address 10.0.0.1 -- if you have the "standard" setup your address might be 192.168.1.1 or .1.2. The DHCP server is enabled for addresses 10.0.0.101 thru 10.0.0.150, but apparently this did not work for this Ubuntu installation):

Configuration: Static IP address

IP address: 10.0.0.61 (pick any unused address not in the DHCP server's enabled range)

Subnet mask: 255.255.255.0

Gateway address: 10.0.0.1 (use your router's LAN address here)

OK

Close

:)

------------------------------

Now, however, after the installation finished, I can't Ping anything, even my own router at 10.0.0.1.

I notice all the settings on the default-installed stuff are IPv6; could this be the problem?

Any help fixing this will be appreciated.

Jim

---

### Post by Jim-BobH on 2007-12-18
Here's the next wrinkle:

I got to thinking, I have done everything I can think of, except reboot, so I did, and now Ping and FF and everything seems to work.

Also, I note that in Network Tools >> Devices, a new line shows, IPv4. Hm-m-m-m.

So, why doesn't the Network setup tool (see my last post) say "must reboot ..." (or restart Networking, whatever)?

IHTH, and I would still like to learn more about what is going on here; I'm mostly guessing instead of reading the User Manual -- does it cover any of this stuff?

Thanks for any help.

Jim

---

