---
title: "[SOLVED] Problems with LTSP after upgrading Edubuntu Server from Feisty to Gutsy"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by myii on 2007-10-23
Prior to upgrading, I had 19 thin clients up and running in our school computer lab.  Since upgrading, I can't have more than around 6 to 8 thin-clients connecting *.  The remainder can't even see the server when attempting to boot over the network.  Those that do connect operate at a much slower speed than before the upgrade.  Since there seemed to be a problem with dhcp, I tried to restart the service but the terminal just hangs.  Even requesting the status of the dhcp service takes a very long time comparatively.  In fact, there are a number of other problems I've noticed, that are seemingly unrelated – one of the main ones is that the server sometimes hangs when I'm logging in, even if I attempt to log in from the console (Ctrl-Alt-F1).

* I've tried to see if only specific clients connect but it seems that after any combination of 6-8 clients connect, the rest fail to find the dhcp server.
 
Now most times I mooch around on the web until I find a solution but I haven't got the time on this occasion; I've already been a day without the lab but I can't afford to lose tomorrow as well – your help is greatly appreciated.

What I'm after:

[LIST=1]
[*]Best case scenario: Someone knows how to get things working without my having to downgrade the server back to Feisty again.
[*]If rebuilding with Feisty is the quickest option, I'd really appreciate if someone could tell me what I need to save before doing so.  I already have /home on a separate partition but I don't fancy having to setup all of the user accounts all over again.
[/LIST]

---

### Post by SpiritIsReality on 2007-11-08
howdy
My mistake. I finally noticed the Reason: Moved to Forum: Installation & Upgrades instead. I was going to ask you how
you solved it. What I saw aysiu say the other day, was that if you click the Report button next to the number of the thread,
a moderator can remove it for you.
trails

---

