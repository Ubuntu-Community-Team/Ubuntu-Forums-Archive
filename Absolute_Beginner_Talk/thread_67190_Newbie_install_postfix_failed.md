---
title: "Newbie install: postfix failed"
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by 117 on 2005-09-19
Hi guys, complete linux newbie here (apart from a brief look at DamnSmallLinux about a year ago, which I didn't like), was looking for an easy and user-friendly Linux system for a colleague and stumbled on Ubuntu, so thought I may as well try it myself while I'm at it, ran the Breezy Live cd and loved it, so just done an install.

First off, I had a problem whereby the install froze during the apt configuration stage at 25% "Primary installation repository", I searched these forums and found a solution, rebooted the PC and then installed as Server, then after rebooting got a command prompt and ran the following
```
sudo aptitude update
``` 
```
sudo aptitude install ubuntu-desktop
``` 

which all ran fine (took quite a while), but at the end i had the following message: 
> Setting up ubuntu-desktop (0.73) ...
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack! Something bad happened while installing packages.  Trying to recover:
Setting up postfix (2.2.4-1ubuntu2) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
postalias: warning: valid_hostname: 192
postalias: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter 
vale: 192
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

I gathered this is a problem setting up my system for mail? and that the problem was that I'd used a numerical hostname?  

So I rebooted again, and after logging in got the graphical desktop, and ran the update thing that popped up, which all ran fine again other than this message at the end:

> E: postfix: subprocess post-installation script returned error exit status 1

So I'm guessing that my install has now all been succesfull, and I just need to configure postfix correctly now for my mail to work?  The question is: how?

---

