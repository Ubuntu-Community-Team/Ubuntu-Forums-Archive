---
title: "I can't Browse!"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by bks on 2007-03-06
I just hooked up my PC via Ethernet and I was able to download the 202 MB of updates, but I can't get FireFox to surf the web.  I checked the connection settings and it is set to "Directly connect to the Internet', that should be correct when using broadband. Right?

---

### Post by Brunellus on 2007-03-06
> **bks said:**
> I just hooked up my PC via Ethernet and I was able to download the 202 MB of updates, but I can't get FireFox to surf the web.  I checked the connection settings and it is set to "Directly connect to the Internet', that should be correct when using broadband. Right?
Slow down and clarify.  How are you connected--cable modem?  ADSL?  University network?

---

### Post by bks on 2007-03-06
Sorry. I am running on a DSL modem.

---

### Post by Brunellus on 2007-03-06
> **bks said:**
> Sorry. I am running on a DSL modem.
is Ubuntu dialing the modem directly?  Is there a router between your modem and the computer?

---

### Post by bks on 2007-03-06
It shouldn't be dialing and the modem is a router as well.  What I don't get is, why can I download updates, but not surf.  That leads me to believe that Dapper is configured correctly and its a browser problem, but unfortunately I don't really know what I'm talking about.

OK, I know I've been a bit sketchy, I appologize.  Here's what I'm working with:

Ubuntu 6.06
10/100 On board Ethernet NIC
ActionTek DSL router/modem

The network settings for Dapper say that eth0 is active and working correctly.  The software update runs automatic checks and returns a list of availible updates and I can download them at 90 kbps.  When I open FireFox and type Google in the address bar, down in the status bar it says 'Connecting to www.google.com' and that is where it stays.

---

### Post by Tomshaq on 2007-03-06
Oddly enough, i have been having similar problems with a newly installed version of dapper on my home pc which i have never had before. It's odd, because i can access the updates and the ubuntu home page in firefox, but no other web pages. I just noticed this last night so i was not able to play around with it too much, but i do know that my connection was active and working.

One interesting thing about this problem is that we are both using an Actiontec modem to access the internet. Maybe there is a compatibility issue?

---

### Post by xael on 2007-03-06
> **bks said:**
> (snip)

The network settings for Dapper say that eth0 is active and working correctly.  The software update runs automatic checks and returns a list of availible updates and I can download them at 90 kbps.  When I open FireFox and type Google in the address bar, down in the status bar it says 'Connecting to www.google.com' and that is where it stays.

Wonder if are there any other web browsers installed in the system?. If there are, then try browsing a bit with them.:confused:

---

### Post by Tomshaq on 2007-03-06
I was thinking of downloading another browser and trying that, but i did'nt have much time. I will probably try that when i get home if noone here has run into this before and has an easy solution. I know that firefox is the only browser that installs with the base by default, but im sure i could dowwnload konqueror or something since downloading seemsto be working...

---

### Post by Tomshaq on 2007-03-06
I just got home and played a little more and found a solution that worked for me, try it out.

In the Firefox address bar type in about:config and filter "ipv6"

toggle the default value so that it is disabled. you should be able to surf the internet freely now!

---

### Post by LookTJ on 2007-03-06
try disabling IPv6.

edit: didn't see your last post. you beat me. good job finding it yourself :)

---

### Post by Chuckanut on 2007-03-13
Thanks guys!!  I've been having the same problems the last few days and it was making me crazy.  Now I can move on to the next issue.

Tom

---

