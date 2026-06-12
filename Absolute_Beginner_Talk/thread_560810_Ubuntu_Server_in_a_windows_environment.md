---
title: "Ubuntu Server in a windows environment"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-09-26
I have a pc that I need to make into a small office server. More like a file server than anything else. what I want to do is use 2 300gb hdds one mirriring the other in case of a hdd failure.  would Ubuntu be a good choice?

---

### Post by cmnorton on 2007-09-27
Other than a file server, what else do you want to host? How old is the hardware? 

We have Ubuntu test machines, running SAMBA, telnetd, and sshd. If I had my way, our production environments would be the same, but we're running a combo of RH 9  RHEL 3, and SCO Unix. All these are all about to go to new hardware and RHEL 4. 

Linux servers in general just keep running without out a lot of falling down. Ubuntu is the easiest so far -- from my experience -- to configure and install non-standard stuff. I don't see any advantage not to get regular Ubuntu and just configure in what you need, unless you subscribe to not running X on a server. Again, Ubuntu has been great for configuration.

---

