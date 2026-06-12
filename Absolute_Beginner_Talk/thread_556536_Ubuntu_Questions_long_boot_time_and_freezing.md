---
title: "Ubuntu Questions: long boot time and freezing"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by BavarianBuilt on 2007-09-21
Hey everyone,

This is my first post of I hope to be many.  I just set up a dual boot on my Thinkpad Z60t laptop with XP pro and Ubuntu 7.04.  I've fallen in love with Ubuntu as I rarely ever boot into Windows.  I've done google and forum searches on these two issues I'm having but have not come up with anything.

First, since setting up a dual boot Ubuntu seems to take a long time to boot.  Windows boots at normal speed but Ubuntu hangs at the loading screen for a good 2-3 minutes before the loading bar even begins to move.  Any ideas as to what could be holding it up.

My next issue is a real annoyance.  This seems to be happening randomly however maybe you guys will know if something is causing it.  Ubuntu seems to freeze at random times.  It could be minutes or hours into when I first booted up my machine.  Nothing responds, I can't move my mouse nor type anything with the keyboard.  Firefox has been running each of the times it's locked up and NetBeans was running a few other times, but not every time.  I'm running v2.0.0.7 of Firefox.

Any help or input on these topics would greatly be appreciated.

Thanks guys!

Gary

---

### Post by LowSky on 2007-09-21
i bet somthing is a little off in you boot files... most likely something you installed and is crashing in the background. The reson it is happening when firefox is open is most likely caused by the amount of resource firefox uses at start up.

My suggestion is to reinstall ubuntu and start fresh instead of looking for files.

---

### Post by jnorthr on 2007-09-21
First of all, welcome to the team :KS

From a terminal command line, you can type
dmesg
then scroll to the bottom to see kernel messages about the load process. You can also use System>Administration>System Log feature to review a number of the logs produced during various steps of the boot process. They may help to diagnose your particular problems.

Do you have a wireless card installed ? My system takes some time to boot if it is trying to hunt out a wireless connection at boo time. I must say that 3-4 minutes still sounds like too long to wait. You can also try
lshw
to look at what ubuntu sees as your hardware config. It may be video card related.

I gave up on firefox as it's too slow and tried opera for a browser. typically keep 10 -15 tabs open at once with no performance issues. This may be an easier option to try than a complete re-install - yet...

---

### Post by LowSky on 2007-09-21
Fireofx is "slow" because its designed to work on both dial up and broadband, dial up doesnt move fast so FF make something more managable but this will make broadband users think its slow. heres the sloution

 ```
1) Open Firefox
2) Type "about:config" into the address bar and hit return. Scroll down and look for the following entries: 
network.http.pipelining network.http.proxy.pipelining network.http.pipelining.maxrequests 
3) Alter the entries as follows: 
Set "network.http.pipelining" to "true" (simply double click the entry) 
Set "network.http.proxy.pipelining" to "true"  (simply double click the entry) 
Set "network.http.pipelining.maxrequests" to some number like 30. This means it will make 30 requests at once. 
Now right-click anywhere and select New-> Integer. Name it "nglayout.initialpaint.delay" and set its value to "0". This value is the amount of time the browser waits before it acts on information it recieves. 
4) Close Firefox
5) Re-open and test for speed 
 
```

---

### Post by BavarianBuilt on 2007-09-21
Thanks for the quick replies guys.  I do have a wireless card enabled when Ubuntu boots.  It's onboard wireless.  Also, I would prefer not to re-install Ubuntu.  I'll dig into these issues using the methods you guys mentioned this afternoon and see if I can come up with some solutions.

---

