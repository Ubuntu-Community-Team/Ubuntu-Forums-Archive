---
title: "Cannot connect to the Internet"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by AP Erebus on 2006-08-10
Hey guys,

I have recently  moved to Linux for uni work and I have had trouble getting on the internet.

I have a wired connection to a NetComm NB5PLUS4W [(Link)](http://www.netcomm.com.au/Wireless/eleveng.php). 

The router assigns my comp a IP address (192.168.1.5) and I know this becuase I checked with the 
```
sudo dhclient eth0
``` and it verified this.

My problem is that when I click on a external link in Firefox, the status bar says it's connecting to the site ([www.google.com](www.google.com), for example) but nothing happens.

None of the other programs that access the net (updater or GAIM) can do it either.

I'm sure I am missing something but this is starting to irritate me.

Many Thanks,
AP

---

### Post by bigken on 2006-08-10
try this in the firefox address bar type about:config and in the filter bar type ipv6 and change from false to true just double click it  ;)

---

### Post by AP Erebus on 2006-08-10
Great, this worked for Firefox...

I still can't get on in GAIM, is there something else I have to run for the whole system to do with ipv6...

I'll google it i think :D

---

### Post by bigken on 2006-08-10
if do search on here for ipv6 1st then google it you will find the answers ;)

---

### Post by AP Erebus on 2006-08-10
Ok, I have disabled ipv6 so when I run that command line thingo it doesn't give any response... but I still cannot connect with anything apart from Firefox.

The Update Manager, GAIM, Evolution Mail all do not connect. This is very irritating.

---

### Post by bigken on 2006-08-11
do a search for dns settings this could be your problem there loads of answers on hear about it ;)

---

### Post by coffeecat on 2006-08-11
To disable IPv6 system wide so that all apps can access the internet, have a look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=87798"). Although it's titled speeding up the internet, it's just as relevant for when you can't resolve anything at all. DNS is a side issue here - your problem is IPv6. But do read well into the thread, especially the comments about the donwside of disabling IPv6.

When I was afflicted by this last year I solved it once and for all by updating my router firmware. Apparently, outdated or badly written router firmware is confused by IPv6 modified IPv4 addressing. Complain to your router manufacturer if they do not have a later version of the firmware, and then complain again. :wink: Look round other forums - it's a common problem, one which has probably lost many potential new users to the world of Linux.

---

### Post by ese on 2006-08-11
Well may i join you on this topic i have similar problem like our friend its like this:
 first of all i am new to this linux os specialy ubuntu but i find it better in some ways than fedora, anyway what my problem here is that i have a windows 2000 server and i was able to connect it and most of the time browse my files in the shared folder i made using the add network place in windos now when i change into ubuntu its quit different although i was able to browse my shared folders in my server and ping to it that its responding and i have my ip address on my pc, when i try to use interent with firefox it displays server cannot be found what is the thing i miss please have your idea. Thanks

---

