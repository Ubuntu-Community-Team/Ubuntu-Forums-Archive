---
title: "Firewall"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by LE CHARBON on 2007-05-02
Because I am in shock over xp, is really needed to have any security/firewall installed on Feisty Fawn??:confused:

---

### Post by gerscht on 2007-05-02
Not really, ubuntu only has the ports open which need to be open anyways.
Do a
```
nmap localhost
``` to see which ports are actually open.
There is a big thread over here: [http://ubuntuforums.org/showthread.php?t=185995&highlight=firewall](http://ubuntuforums.org/showthread.php?t=185995&highlight=firewall)

Gerscht

---

### Post by starcraft.man on 2007-05-02
Ummm, I believe there is a very basic firewall in place on Ubuntu by default. If your behind a NAT router (highly advisable) then you are much safer than trusting a firewall (not that they don't work, but a hardware router can't be turned off or hacked if configured right). NAT routers make you invisible on the net and will protect anything from even attempting access to your PC. I wouldn't worry much about virusses and other bad things on linux though.

You can always install firestarter: [Here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Firewall_.28Firestarter.29")

Make sure you know what your doing when you config it though.

---

### Post by taurus on 2007-05-02
You should have iptables, firewall, running at boot so if you want to configure it, you can use firestarter to do that.

---

### Post by az on 2007-05-02
The linux kernel handles all packets.  It can use a set of rules (iptables) to filter them.

In windows, an application-based firewall will talk to the windows OS and try to keep tabs on what apps are talking to the network.  Unfortunately, this is not comprehensive and a lot of stuff can get throught without you knowing about it.

In GNU/Linux, everyting is transparent.  Since the software is uploaded to the repositories in source form and compiled by the autobuilders, and since not just anyone can get priviledges to upload there, the chance of you installing and running any malware is very very slim.  You can also know what is listening to the network at all time without needing to install additional software to do that.

Just keep up-to-date with software updates and forget about anti-virus, anti-spyware, firewalls and all that.  They do not apply to Ubuntu.

---

### Post by LE CHARBON on 2007-05-02
What would be a good NAT router that works well with Feisty? I have a DSL modem. I use a Dell Dimension w/ Pen 4 2.8 GHZ and 1GB of RAM, if that helps. Thanks for the help.:)

---

### Post by starcraft.man on 2007-05-02
> **LE CHARBON said:**
> What would be a good NAT router that works well with Feisty? I have a DSL modem. I use a Dell Dimension w/ Pen 4 2.8 GHZ and 1GB of RAM, if that helps. Thanks for the help.:)

Any router that you buy today or was made within the last 4 years I believe come with NAT built in. My personal preference is a Linksys WRT54GS, it has both wireless capabilities and four wire ports to connect pcs by ethernet. Not to mention it has great support with hacking. I'd go with that. I think you can find it pretty cheap now too.

---

### Post by motang on 2007-05-02
> **az said:**
> The linux kernel handles all packets.  It can use a set of rules (iptables) to filter them.

In windows, an application-based firewall will talk to the windows OS and try to keep tabs on what apps are talking to the network.  Unfortunately, this is not comprehensive and a lot of stuff can get throught without you knowing about it.

In GNU/Linux, everyting is transparent.  Since the software is uploaded to the repositories in source form and compiled by the autobuilders, and since not just anyone can get priviledges to upload there, the chance of you installing and running any malware is very very slim.  You can also know what is listening to the network at all time without needing to install additional software to do that.

Just keep up-to-date with software updates and forget about anti-virus, anti-spyware, firewalls and all that.  They do not apply to Ubuntu.

I couldn't say it better myself!
:lolflag:

---

