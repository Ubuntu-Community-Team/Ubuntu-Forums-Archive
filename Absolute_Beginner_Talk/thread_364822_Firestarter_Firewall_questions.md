---
title: "Firestarter Firewall questions"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by SVDtiger on 2007-02-18
hi, im sight challenged so there is very good chance i have blundered with some setting or something to do with my firewall. it starts up fine but as of lately shows no data in the events window. and with my local dialup pool i know their is inbound action but now i cant see anything

for an activity and some fun i try to play an online game called astro empires but cannot stay in the game without it kicking me. im curious now if the 2 are related. maybe i have firestarter set incorrectly and the game needs something according to its admin or im being attacked and kicked out. im not losing my net connection just my connect to said game. and only there does it happen

is there any way to restore default settings and/ or  restart firestater from command line like i have to do with firefox quite frequently??

sorry to be a pain  and please know im very grateful for any guidance. john

---

### Post by chggr on 2007-02-19
The firewall and its user interface are two totally different things. Even if you don't see firestarter on your panel, the firewall is probably running on the background and saving you from a lot of port scans. If you want to start the firewall but not the user interface, open a Terminal and type in:

sudo /etc/init.d/firestarter start

If you want to stop the service, run the same command replacing start with stop.

I personally have configured firestarter to start automatically every time I connect to the Internet. This can be done by clicking on "Preferences" -> Firewall -> Start/Restart firewall on dial out. I use the Graphical User Interface (GUI) only when I want to make some changes in the configuration of the firewall.

About the events list: Don't worry, it has happened to me too. But it's nothing to worry about because the firewall works OK in the background, even if this doesn't show on the events list. On the other hand, sometimes the list gets too full and firestarter is consuming 100% CPU. That's why I don't prefer having the GUI of firestarter always open and minimized on the panel.

About the pc game:
Probably you havent opened the right ports on the firewall. You can do that by creating a rule on the Policy tab, but first you need to know what port does the game require to be opened.

You can test your computer's safety in the following URL:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

