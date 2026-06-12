---
title: "User Settings, Network Settings, Gedit not responding"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by rahulbasu on 2007-12-01
When I try running system>administration>users and groups, the window opens up, but I don't see anything in the window (after I enter my password). When I try to close the window, I get a message, "User Settings is not responding".

I have a similar problem when I try system>administration>network

If I open a terminal window, & I try sudo gedit /etc/modprobe.d/blacklist (I need to do this to blacklist rtl8187 to install a netgear wifi dongle), the gedit window opens but I have the same problem.

I guess I am not getting full rights as root.

I am running Feisty Fawn, which I installed - I had the earlier version of Ubuntu earlier.

If I go to the terminal window and run "users", I get rahul rahul (basically my ID twice).

Its an Intel Pentium 3.0 GHZ dual core.

Any ideas /

---

### Post by Trevorius on 2007-12-02
I have the same problem with network settings. Anytime I try to access it, it comes up as a blank dialogue box that I can't close without forcing it. I certainly hope to find some sort of resolution to this as it's such a constant issue.

---

### Post by A-dogg on 2007-12-03
Have you found a resolution to the Network Settings window coming up as blank that you're unable to close? Now I'm getting this issue.

Thanks.

---

### Post by rahulbasu on 2007-12-04
It was a fairly recent install, so I just reinstalled it. I think what may have happened is that it took my Windows XP profile at the time of installation, and that messed up some permissions - sudo worked sometimes, and sometimes it didn't.

My windows hard disk crashed, so I needed to get Ubuntu working with Wifi, when I ran into all this.

Haven't yet got the wifi working, but this problem hasn't appeared since the reinstallation.

Rahul

---

### Post by Trevorius on 2007-12-07
> **A-dogg said:**
> Have you found a resolution to the Network Settings window coming up as blank that you're unable to close? Now I'm getting this issue.

Thanks.
I've switched to wicd which seems to work ok.

---

### Post by A-dogg on 2007-12-07
yep, me too.

---

### Post by johnfarrow on 2008-01-31
Please forgive the ignorance... but what is wicd?

---

