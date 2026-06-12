---
title: "firestarter suddenly stops running..."
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-10-29
hi i've installed ubuntu gutsy for the first time,so i'm kind of new in linux...,all the installation process was fine.
Then i installed some other apps including firestarter. Everything seems to work fine but sometimes when i'm online firestarter suddenly dissapears....and stops running. Why?

---

### Post by Octavgmail.come on 2007-10-29
me too.

---

### Post by ggaaron on 2007-10-29
Don't use firestarter, it is several years old and it is not updated any more, it's a dead project.

---

### Post by Dr Small on 2007-10-29
> **ggaaron said:**
> Don't use firestarter, it is several years old and it is not updated any more, it's a dead project.
It still works good though.
I don't keep it running, since it only configures iptables...

someoneouthere, don't I recall you making a thread similar to this, about an hour ago ?

---

### Post by bodhi.zazen on 2007-10-29
Not sure why it is crashing, but here is some information on firewalls :

Firewall FAQ

Firewall Information.

The Ubuntu (Linux) firewall is called IP tables and is included with your Ubuntu installation.

The default settings are permissive (meaning they allow all traffic) and, if you are not running a server, you may feel this is adequate protection.

If you would like to configure your firewall the two options are to use a gui front end or write IP rules for yourself (there are various scripts on the web that will help with this).

The most popular gui tools are Firestarter and Guard dog (KDE). Keep in mind that these applications are not firewalls, but rather configuration tools. This is sometimes a source of confusion as the application should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest :twisted:.

See these links for further information/how to use these tools :

[center][[color=red][Size=6]How to Firestarter[/size][/color]](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html) - [[color=blue][size=6]How to Guard Dog (KDE)[/size][/color]](http://www.simonzone.com/software/guarddog/manual2/index.html)[/center]

Firestarter Home Page : [http://www.fs-security.com/](http://www.fs-security.com/)

**Default Firestarter Policies**:
> [list][*]New inbound connections from the Internet to the firewall or client hosts are blocked.
[*]The firewall host is freely allowed to establish new connections.
[*]All client hosts are allowed to establish new connections to the Internet, but not to the firewall host.
[*]Traffic from the Internet in response to connection requests from the firewall or client hosts is allowed back in through the firewall.[/list]

If you would like to learn more about IP tables, here are some starting points:

_**Iptables references_** :
[list][*][https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[*][http://www.linuxguruz.com/iptables/howto/](http://www.linuxguruz.com/iptables/howto/)
[*][http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)[/list]

If you would like to learn more about basic Ubuntu security, please see this thread :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

If you would like to debate/discuss the use of firewall, please post here:

[ Recurring Discussions](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by ggaaron on 2007-10-29
Dead projects shouldn't be encouraged for new users. Maybe it still works, but any error shouldn't be a surprise.

---

### Post by bodhi.zazen on 2007-10-29
> **ggaaron said:**
> Dead projects shouldn't be encouraged for new users. Maybe it still works, but any error shouldn't be a surprise.

Why do you assume the problem is with Firestarter ?

Do you have a link ? This is the first I have heard of Firstarter being "Dead".

Have you consider recommending an alternate ?

If a package is not working one should file a bug report : [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

### Post by ggaaron on 2007-10-29
[http://en.wikipedia.org/wiki/Firestarter_%28firewall%29](http://en.wikipedia.org/wiki/Firestarter_%28firewall%29)

Latest is form January 2005, and iptables changed quite a bit from what I know from this time.

Unfortunately I can't recommend any alternative, some time ago I've checked many "graphical iptables configurators" and none were easy+fully working, I've decided to edit iptables myself. This is unfortunate, I know that editing text files is not what people like, so I can't recommend any alternative application.

---

