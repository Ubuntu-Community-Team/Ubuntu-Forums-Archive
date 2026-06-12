---
title: "Am I being Hacked?"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by g_butler2000 on 2006-02-27
I'm n00b to Linux and installed Ubuntu on Saturday.  I was looking through the gui and  found system logs.  While I was there I stumbled across a place where it looked like someone was binding an IP address to me and I saw alot of the following?

localhost gdm[6548] (pam_unix) session closed for user gary2570
localhost su[7239] (pam_unix) session closed for user root
localhost gdm[6535] (pam_unix) session opened for user gary2570 by (uid=0)
localhost CRON[7780] (pam_unix) session opened for user root by (uid=0)
localhost CRON[7780] (pam_unix) session closed for user root

#1 Does someone have control of my system?
#2  IF #1 = yes then how do I get them out?
#3 IF <> 1 or 2 can you explain what these entries are for?

Thanks,

Gary

---

### Post by Zeroangel on 2006-02-27
It looks all good to me. The system needs to run certain applications under root, so it usually has all that set up beforehand. "Su" for example, is designed to run several commands under root, and might have something to do with initialization scripts (ie: for bootup), "CRON" is an application similar to Windows Task Scheduler, and so too needs to run under root. "gdm" is a process that happens prior to logging in, GDM usually renders the login screen and deals with other login details.

So from this, I gather, these events are happening as you are starting the machine. Therefore it is natural for some processes to login under root to get things done.

You can't really hack into a linux computer unless you know its password, so if a hacker was trying to get in he would likely be using the 'bruteforce' method which is just basiclaly having a program guess passwords. In that case, you would see a bunch of incorrect logins logged. The thing is it's very difficult to even get terminal access from a remote machine unless you have chosen to install a program that allows that.

---

### Post by az on 2006-02-27
[QUOTE=g_butler2000]

localhost gdm[6548] (pam_unix) session closed for user gary2570
[/QUOTE]

gdm needs root priviledges to be able to log any user in.  This is normal.

[QUOTE=g_butler2000]localhost su[7239] (pam_unix) session closed for user root
[/QUOTE] 

You typed sudo su at a console and then did stuff.  You can also just use sudo for each command and you get the same effect, along with every command being logged.  That's great for tracking down problem you cause yourself....

[QUOTE=g_butler2000]localhost gdm[6535] (pam_unix) session opened for user gary2570 by (uid=0)
[/QUOTE]
Gdm again.


[QUOTE=g_butler2000]localhost CRON[7780] (pam_unix) session opened for user root by (uid=0)
[/QUOTE]

There are a few cron jobs (jobs that get done at a certain time)  Like compressing log files and so forth.

[QUOTE=g_butler2000]localhost CRON[7780] (pam_unix) session closed for user root
[/QUOTE]

Ditto.


If you keep up to date with your security updates (breezy-update and breezy-security repositories) and do not install software willy-nilly, you should be quite secure.

---

### Post by g_butler2000 on 2006-02-27
Thanks!  Someone told me the name Pam_UNIX was a utility that ran in the background.  I saw all of those and I immediately thought someone was trying to get me.  HAHA  

I appreciate your help.

---

### Post by jinacio on 2006-03-11
hmm, anyway to disable logging of these messages?

---

