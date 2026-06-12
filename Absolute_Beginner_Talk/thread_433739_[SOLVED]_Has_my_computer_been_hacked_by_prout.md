---
title: "[SOLVED] Has my computer been hacked by prout?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-05-05
Hey guys,

Something strange is happening to my computer every now and then after I've entered my login info. The screen goes black, and some strange writings come up:

> chroot
chroot
prout
prout

hack chroot prout
hacked by prout

Then the hard disk starts going crazy, like an helicopter at take off, spinning indefinitely. When I force the computer to restart, the old Ubuntu is back and running.

In Windows XP, Norton doesn't detect anything. What should I do? :confused:

---

### Post by tophatandy on 2007-05-05
try installing the virus scanner in the repos or just install avg free for linux, run a quick scan and see what comes up.

---

### Post by GrueTamer on 2007-05-05
> **the8thstar said:**
> In Windows XP, Norton doesn't detect anything. What should I do? :confused:Windows XP won't detect anything because it doesn't recognize linux partitions.

Do what tophatandy said, get some virus protection, whatever happened to you is a little fishy.

---

### Post by mikewhatever on 2007-05-05
chkrootkit is in the repositories, try that too. To run it, type 'sudo chkrootkit' in the terminal

---

### Post by tophatandy on 2007-05-05
here is the download page for avg free.

[http://free.grisoft.com/doc/5390/lng/us/tpl/v5#avg-anti-virus-free](http://free.grisoft.com/doc/5390/lng/us/tpl/v5#avg-anti-virus-free)

I would also consider installing firestarter if you do get anything comes up on the virus scan.
How often does this happen? (every other time, sometimes, or is this the first time?)

Do you use DSL, Broadband, or dial up?
If it was actually a hack then:

if you use broadband or dsl most modems come standard with some sort of security software such as a NAT or someother sort of firewall.  I would consider beefing this up a bit especially if you have Broadband (Internet comes in through cable). DSL typically has dynamic routing in the case of most Internet service providers, so every time that you reset your modem you get a new IP. If you have DSL beef up your security and restart your modem.

If you have dial up you have dynamic IP's so you dont really have to worry about him visiting you again if you are worried about that. 

I will be watching the post if you have any questions.

-tophatandy

---

### Post by the8thstar on 2007-06-17
Sorry for posting so late in reply to all of your good advice... Eventually, I was never able to find out the cause of my problem. I just reinstalled U7.04 and since then my problem has disappeared.

---

### Post by ecs_pf5 on 2007-06-17
I went to try AVG earlier on but got a message 'wrong architecture'.. kinda forgot i have the 64 bit version of Feisty installed.

Is there much in the way of antivirus for x64? just out of interest. I read a lot of people say one doesn't need antivirus on Linux as much as one does on windows

---

### Post by ShareBuntu on 2007-06-17
Make sure you also get rkhunter.

```
sudo aptitude install rkhunter
sudo rkhunter --update && sudo rkhunter -c
```

---

