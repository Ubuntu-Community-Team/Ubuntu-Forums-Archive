---
title: "eth0, ntp, ntpdate issues during boot"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by movrshakr on 2007-12-17
This was in another area of forums, but no responses at all there.

I have ntp set up on my machine (there is a minor problem with it...see further below). Realizing  that ntp will fail (exit) if the system hardware clock is >1000 seconds different from the ntp-gathered time, I tried to set up some protection for that event, which can conceivably happen if you have a bad clock, or computer is off for months, or cmos battery is dead, or idiot manually set the hw clock wrong, etc.  You wouldn't know it unless you happened to catch it reading syslog.  So I began searching for a way to prevent  this, and found it at 
[http://nixtechnica.blogspot.com/2006/09/how-to-synchronize-time-with-ntp.html](http://nixtechnica.blogspot.com/2006/09/how-to-synchronize-time-with-ntp.html)
.
I implemented this: 
a. Created /etc/init.d/ntpdate file which contains: 
#! /bin/sh
echo "Synchronizing system time with Ubuntu Servers..."
ntpdate ntp.ubuntu.com
echo "Setting hardware clock to updated time..."
hwclock --systohc
.
b. Then this : sudo chmod 700 /etc/init.d/ntpdate
. 
c. Then this: sudo update-rc.d ntpdate defaults 90 

This "kind of" worked, except for the following problem which is my question for how to fix...(and I have temporarily done an ntpupdate remove, so it is now not in any runlevels.)

When I boot, and look at syslog, it says that ntpdate failed because the port was in use.  I also note that eth0 startup tries 8 times going through Stage 3, and completes Stage 4-5 on the 9th try.  But ntp started whe eth0 was not up, so it did not find any servers to sync to.

Bottom line: how do I make the above solution work, or does someone have a different guaranteed solution to, at boot, run ntpdate (to set current system time right), then run "hwclock --systohc" to write a good time into the bios clock? AND to get ntp to start when it can actually make connections.  These two things may or may not be related.
.
Sorry to be a little long, but I wanted to be clear.

---

