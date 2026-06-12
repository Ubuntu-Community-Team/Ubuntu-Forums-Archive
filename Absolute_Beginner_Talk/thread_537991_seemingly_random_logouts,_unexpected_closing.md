---
title: "seemingly random logouts, unexpected closing"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by univremonster on 2007-08-29
I have had a problem recently which has been getting steadily worse.  Occasionally, my Firefox would just shut off.  It didn't freeze, or have some sort of error message, it would just disappear without a sound.  It wasn't a big deal because I could restart it and restore session, and usually I didn't lose anything.  That started oh maybe 3 months ago.

In the following few months, I started having the same problem with other programs.  I played the game "Freeciv" plenty, and it would close on me every few days.  Then Open Office started crashing, and evince, and everything else.  The only one that I've noticed is almost always on and never crashes is XMMS.

In the last month or so, the same thing happens (though this may be unrelated because it is such a different beast) with my login.  I will be working along, writing an email or something, and poof I'll be logged out.  No errors or anything, I'm just typing one minute and staring at the login screen the next.  I'm not proficient enough with Ubuntu to know how to check what just happened.  This morning, I turned off Desktop Effects in the hope that would make things a little more stable, and nothing has happened thus far, though I would say the average period between those events is about 2 or 3 days, so time will tell.

About the OS:  I am running Fiesty Fawn, which I upgraded to twice (started with Dapper Drake).  I have what I understand to be a fairly common error at login involving IO-APIC, if it's important let me know and I can paste it in here.  About the hardware:  I have a fairly standard 64-bit computer built fairly recently.  I use the proprietary NVIDIA graphics accelerator in the Restricted Drivers section.

---

### Post by univremonster on 2007-08-30
update:  1 day into not having desktop effects disabled and this problem has not recurred.  I have both KDE and Gnome, and I have been using KDE today.  Any ideas?

---

### Post by univremonster on 2007-09-04
I am still having this problem in KDE...

---

### Post by tak1150 on 2007-09-04
Would this thread help you? It may be related, may be not...

[http://ubuntuforums.org/showthread.php?t=504858](http://ubuntuforums.org/showthread.php?t=504858)

---

### Post by univremonster on 2007-09-04
I don't have any problems with the speed of the programs or startup time, the problem is that they keep closing without warning.  Did I miss something in the link you left?

---

### Post by tak1150 on 2007-09-04
> **univremonster said:**
> I don't have any problems with the speed of the programs or startup time, the problem is that they keep closing without warning.  Did I miss something in the link you left?

You probably didn't miss anything. I just thought that this feisty bug using too much of your RAM may have something to do with it.

---

### Post by univremonster on 2007-09-05
I could see how this could be a problem... on my Gnome system monitor it shows memory usage at 31.8% while I'm typing this, so possibly when more things are going on it gets overloaded... I will give it a try

EDIT:  Turns out that this bug was not the problem.  My /etc/hosts reads 

127.0.0.1 localhost remonster-desktop
127.0.1.1 remonster-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Deedlit on 2007-09-05
Just so you don't feel in anyway insane, it happens to me with the same frequency that you seem to be having it.  I've only had my computer two weeks, it happens with firefox, with gaim, rythmbox, and a couple of others. And I'm sorry to say, I don't have an answer either.

---

### Post by univremonster on 2007-09-06
> **Deedlit said:**
> Just so you don't feel in anyway insane, it happens to me with the same frequency that you seem to be having it.  I've only had my computer two weeks, it happens with firefox, with gaim, rythmbox, and a couple of others. And I'm sorry to say, I don't have an answer either.

Thanks for the support, Deedlit.  Since it's not just me and you're on a fresh install I will try to post this as a bug.

In order to help out the people fixing bugs, can anyone tell me how to find any error logs my computer generates?  The only tool I have been using is gnome-system-monitor, which isn't very verbose.

---

### Post by univremonster on 2007-09-10
update:  I just got around to posting this.  The bug is at [https://bugs.launchpad.net/ubuntu/+bug/138739](https://bugs.launchpad.net/ubuntu/+bug/138739)

---

### Post by snifer on 2007-09-10
If you're using an nvidia card, may be it could be related to this bug: [https://bugs.launchpad.net/bugs/121486](https://bugs.launchpad.net/bugs/121486)

---

### Post by univremonster on 2007-09-11
Thanks for the link, I have posted a comment that the two may be related.  This is the first time I've dealt with the bug tracking/fixing, hopefully they're fairly prompt as it's a fairly infuriating problem.  In the meanwhile I may try using a different web browser...

---

