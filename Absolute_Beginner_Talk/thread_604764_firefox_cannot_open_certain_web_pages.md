---
title: "firefox cannot open certain web pages"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by higuava on 2007-11-06
I am new to Linux. I am using Ubuntu 7.10 and the latest Firefox.
I cannot open some of the web pages, such as this one:
[http://tools.cisco.com/RPF/register/register.do](http://tools.cisco.com/RPF/register/register.do)
Firefox just tries to load it and never comes back. I noticed this happen to some of the dynamic web pages. Is this a bug or a setting thing?

Can somebody help?
Thanks a lot!

---

### Post by twiceasworn on 2007-11-06
That page loads fine for me with firefox...  Are you using any extensions?

---

### Post by Falc7 on 2007-11-06
works fine for me to

---

### Post by Arthur Archnix on 2007-11-06
It loads for me as well. Make sure you're not running "noscript" extension.

Some troubleshooting things you can do:

1. Try loading the page by hitting Ctrl+F5
2. Try clearing your browsers cache
3. Try removing firefox and reinstalling it.
```
sudo apt-get --purge remove firefox
sudo apt-get install firefox
```

---

### Post by higuava on 2007-11-06
No extensions.

---

### Post by Seisen on 2007-11-06
Its not a Java problem because I just checked try running firefox in safe-mode and go to that website.

```
firefox -safe-mode
```

---

### Post by higuava on 2007-11-06
I only have google tool bar and ubuntu extension. I disabled them and still can't load the page.
I tried all following. Still no luck.

> **Arthur Archnix said:**
> It loads for me as well. Make sure you're not running "noscript" extension.

Some troubleshooting things you can do:

1. Try loading the page by hitting Ctrl+F5
2. Try clearing your browsers cache
3. Try removing firefox and reinstalling it.
```
sudo apt-get --purge remove firefox
sudo apt-get install firefox
```

---

### Post by tubasoldier on 2007-11-06
Internet Explorer can not view this web page.

[http://immike.net/scripts/ie_crash.html](http://immike.net/scripts/ie_crash.html)

The door swings both ways

---

### Post by higuava on 2007-11-06
I knew this long time ago. But this is different. The web page that I am trying to open is a real page. I had to restart the system into Vista and use IE to open the page and switch back to Ubuntu.

> **tubasoldier said:**
> Internet Explorer can not view this web page.

[http://immike.net/scripts/ie_crash.html](http://immike.net/scripts/ie_crash.html)

The door swings both ways

---

### Post by glennric on 2007-11-06
Back up your personal firefox profile by moving .mozilla to .mozilla.bak and restart firefox.  Then try the webpage.  If it works then you have an issue in your personal settings.  I have had this happen before.

---

### Post by higuava on 2007-11-06
Just tried that. It still doesn't work. But thanks a lot for tyring to help.

> **glennric said:**
> Back up your personal firefox profile by moving .mozilla to .mozilla.bak and restart firefox.  Then try the webpage.  If it works then you have an issue in your personal settings.  I have had this happen before.

---

### Post by Arthur Archnix on 2007-11-06
1. Have you tried installing a different browser? In add/remove click on internet, and install epiphany, and opera. Try again.

2. Still have problems? Could be a firewall. Have you installed firestarter?

---

### Post by higuava on 2007-11-07
Thanks a lot for the help!
So I installed Epiphany and it has the same problem.
I haven't knowingly installed any firewall. I typed firestarter in a terminal and it says firestarter is not installed.
Where should I look for the firewall?

> **Arthur Archnix said:**
> 1. Have you tried installing a different browser? In add/remove click on internet, and install epiphany, and opera. Try again.

2. Still have problems? Could be a firewall. Have you installed firestarter?

---

### Post by pdan on 2007-11-07
Could be your router.  I had a similar problem with my Linksys router.  When I upgraded the firmware, all was fine.  btw, the page loads fine for me in firefox

---

### Post by Slipmyknot101 on 2007-11-07
Well to be sure that you do not have any firewall software installed, the best thing I can think of is to navigate to Synaptic Package manager, search both title and description for "firewall", sift through the roughly 120 results.

Here are some things to double check to make sure are not installed:

1. Shorewall
2. Fiaif
3. firehol
4. firestarter
5. fwbuilder
6. glacier2
7. guarddog

---

### Post by higuava on 2007-11-07
If I reboot the machine into Vista, I don't have this problem. Can this fact rule out router?
Thanks.

> **pdan said:**
> Could be your router.  I had a similar problem with my Linksys router.  When I upgraded the firmware, all was fine.  btw, the page loads fine for me in firefox

---

### Post by higuava on 2007-11-07
Searching "firewall" results in 118 hits. Only packages are install: iptables and wget. 

> **Slipmyknot101 said:**
> Well to be sure that you do not have any firewall software installed, the best thing I can think of is to navigate to Synaptic Package manager, search both title and description for "firewall", sift through the roughly 120 results.

Here are some things to double check to make sure are not installed:

1. Shorewall
2. Fiaif
3. firehol
4. firestarter
5. fwbuilder
6. glacier2
7. guarddog

---

### Post by Arthur Archnix on 2007-11-07
Yes, if you can access this site from Vista on the same computer then it's not your router.

I'm not too surprised that epiphany can't view the page, as it uses the same engine as firefox. If opera can't do it, then I'd be surprised.

The point isn't that you should install a firewall, it's whether you already have made any changes to the default one that comes installed. Post the output of 
```
sudo iptables --list
```

---

### Post by higuava on 2007-11-09
I installed opera. It can't load [http://tools.cisco.com/RPF/register/register.do](http://tools.cisco.com/RPF/register/register.do) either.

higuava@ubuntu:~$ sudo iptables --list
[sudo] password for higuava:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

Thanks for the help.

> **Arthur Archnix said:**
> Yes, if you can access this site from Vista on the same computer then it's not your router.

I'm not too surprised that epiphany can't view the page, as it uses the same engine as firefox. If opera can't do it, then I'd be surprised.

The point isn't that you should install a firewall, it's whether you already have made any changes to the default one that comes installed. Post the output of 
```
sudo iptables --list
```

---

### Post by Arthur Archnix on 2007-11-10
Ok, your firewall rules are the same as mine and I can access the site. Let's just review here, because I almost feel like we must be missing something. This isn't making sense.
```

1. You're trying to access this site: [http://tools.cisco.com/RPF/register/register.do](http://tools.cisco.com/RPF/register/register.do)
2. You can access it from Vista on the **same computer** (dual boot) without any problem.
3. You don't have problems visiting any other sites (that you know of so far).
4. Neither firefox, epiphany nor opera will let you load that page.
5. No on else on this forum has had any problems viewing that site.
6. You firewall is not blocking you, because it's the same as mine and I can access the site.
```
So, the problem is with Ubuntu, not your browser, or your router. I'm just gonna start making some guesses here, and hopefully someone else recognizes what the problem is, because I'm truthfully baffled.

First, make sure you have java installed on Ubuntu.

Second, have you disabled anything or made any changes to your internet setup? Things like blacklisting ip ranges to tweak firefox, disabling ipv6, or anything else? Have you added an ipfilter.dat file to your system for p2p and torrent applications?

Third, email the site and let them know you can't access it and see if they know why that might be. 

Fourth, toss in an ubuntu live cd and try and visit that site. Does it work?

---

### Post by richiewrt on 2007-11-10
try 
```
ping -c 3 www.yoururlhere.com 
```

this should tell you if its a connection issue, or a display issue, good place to start

---

### Post by Arthur Archnix on 2007-11-10
> **richiewrt said:**
> try 
```
ping -c 3 www.yoururlhere.com 
```

this should tell you if its a connection issue, or a display issue, good place to start

Maybe. But I tried to ping the site and couldn't, even though I could access it without problem. Maybe I was doing it wrong, but all you've done different is tell it to stop after 3 responses, so I dunno.

---

### Post by richiewrt on 2007-11-10
ok, try```
traceroute tools.cisco.com

```

if you were unable to ping it , I would guess that it is an outside issue since you can connect to the internet.

---

### Post by richiewrt on 2007-11-10
nevermind, im half asleep, since you can connect in vista then it is def not a connection issue.

---

### Post by higuava on 2007-11-13
Thanks for the effort.

> **richiewrt said:**
> nevermind, im half asleep, since you can connect in vista then it is def not a connection issue.

---

### Post by alienexplorers on 2007-11-13
Try reading this:
> [http://kb.mozillazine.org/Problematic_extensions](http://kb.mozillazine.org/Problematic_extensions)

---

### Post by higuava on 2008-03-29
> **Arthur Archnix said:**
> Ok, your firewall rules are the same as mine and I can access the site. Let's just review here, because I almost feel like we must be missing something. This isn't making sense.
```

1. You're trying to access this site: [http://tools.cisco.com/RPF/register/register.do](http://tools.cisco.com/RPF/register/register.do)
2. You can access it from Vista on the **same computer** (dual boot) without any problem.
3. You don't have problems visiting any other sites (that you know of so far).
4. Neither firefox, epiphany nor opera will let you load that page.
5. No on else on this forum has had any problems viewing that site.
6. You firewall is not blocking you, because it's the same as mine and I can access the site.
```
So, the problem is with Ubuntu, not your browser, or your router. I'm just gonna start making some guesses here, and hopefully someone else recognizes what the problem is, because I'm truthfully baffled.

First, make sure you have java installed on Ubuntu.

Second, have you disabled anything or made any changes to your internet setup? Things like blacklisting ip ranges to tweak firefox, disabling ipv6, or anything else? Have you added an ipfilter.dat file to your system for p2p and torrent applications?

Third, email the site and let them know you can't access it and see if they know why that might be. 

Fourth, toss in an ubuntu live cd and try and visit that site. Does it work?

Thanks a lot for your help.
It's been several months now and the problem still exists.
Since then, I installed Mandriva, Fedora 8 on the same computer. They all have the same problem. I am now using Ubuntu 8 beta with Firefox 3 beta. The problem is still there. So it seems that this is not a Ubuntu problem, but a Linux problem.
Yes, I have java 1.6 installed on my computer.
My Ubuntu 8 is freshly installed. The only thing I did to the entire system was installing Adobe Flash player plugin in Firefox.
I tried Ubuntu 8.04 live CD and I couldn't load that damn web page.
I use Verizon DSL with Verizon provided Westtell router. I don't remember I did any custom setting on the router.

---

### Post by Hutom on 2008-03-30
> Since then, I installed Mandriva, Fedora 8 on the same computer. They all have the same problem. I am now using Ubuntu 8 beta with Firefox 3 beta. The problem is still there. So it seems that this is not a Ubuntu problem, but a Linux problem.

 
But how come its a linux problem? I am using gutsy and can cleanly open the page. We must be missing something. May be missing for a very long time. But missing. Something must be blocking that site. I remember my friend was unable to open gmail at some point with XP. We still could not find the reason. But there must be a reason. He finally reinstalled his connection. Its working fine now.

---

### Post by N1N31NCHN41L5 on 2008-03-30
Page loaded fine for me. Like they said try uninstalling and reinstallin firefox in the terminal.

---

### Post by higuava on 2008-03-30
> **Hutom said:**
> But how come its a linux problem? I am using gutsy and can cleanly open the page. We must be missing something. May be missing for a very long time. But missing. Something must be blocking that site. I remember my friend was unable to open gmail at some point with XP. We still could not find the reason. But there must be a reason. He finally reinstalled his connection. Its working fine now.

If you read the entire thread, it will be clear for you that it is logical to assume the problem is related to Linux.
By the way, I uninstalled and installed firefox multiple times, from command line or otherwise.

---

### Post by sparkwang on 2008-04-26
I have the same problem, whether I installed 7.10 or 8.04!:(

I can ping the web host, and I can use pidgin to login QQ, but can not open the site.

---

### Post by cindylivengood on 2008-04-26
> **tubasoldier said:**
> Internet Explorer can not view this web page.

[http://immike.net/scripts/ie_crash.html](http://immike.net/scripts/ie_crash.html)

The door swings both ways

What was the purpose of this?  I am a noob... VERY noob, only 5 days old!  I clicked that link.

---

