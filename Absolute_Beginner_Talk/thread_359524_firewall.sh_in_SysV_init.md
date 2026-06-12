---
title: "firewall.sh in SysV init"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by cidhus on 2007-02-12
Moving to Ubuntu from Slackware which uses a BSD init scheme. The SysV scheme has me totally baffled.

I know Ubuntu hasn't any listened to ports by default, but when I open my so few ports, I'd like a simple firewall script run on boot. Where do I put the firewall.sh script that contains my iptables commands. When do I prepend the Snn and Knn to the script name? That kind of thing.

I could call the script from within rc.local, but that seems lame and I'm not sure it would get called in both runlevels 3 and 5.

I've spent most the evening (last five hours) searching with no strikes other than use Firestarter or Guarddog. I so hate GUI frontends of which I have no inkling what they are doing on the backend. I'm really a console type of person.

A hint or a point in the right direction would be appreciated. I'm not afraid to read, albeit slowly and repetitively. Of course, a step-by-step procedural guide would be like winning the lottery.

Running Linux since 1995 (Slackware 1.3, Linux kernel 1.2). Damn, I've become my grandfather.

/herbc

---

### Post by energiya on 2007-02-12
> **cidhus said:**
> Moving to Ubuntu from Slackware which uses a BSD init scheme. The SysV scheme has me totally baffled.

A funny thing... after a couple of months, I've decided to install a Slackware based distro (Zenwalk) and I'm loving it. Actually the only Linux distro on my PC now... anyway... it took me a full day to understand the basics for configuring my firewall (don't like working with GUI when it comes to do important configs) after being used to Ubuntu.

> **cidhus said:**
> 
Running Linux since 1995 (Slackware 1.3, Linux kernel 1.2). Damn, I've become my grandfather.

=D> :wink: 

Found these (hope it helps):
- [this seems what you're looking for]("http://ubuntuforums.org/showthread.php?t=159661") 
- [link 4]("http://www.ubuntuforums.org/showpost.php?p=1882492&postcount=1") (on the forums)
- [link 1]("http://www.howtoforge.com/linux_iptables_sarge")
- [link 2]("http://www.debuntu.org/iptables-how-to-share-your-internet-connection-p4")
- [link 3]("http://librenix.com/?page=Firewall&nextart=8")

---

