---
title: "Disappointed - Need help with modem"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by pcawdron on 2006-10-20
:-? 

Please don't get me wrong, I don't mean to be ungrateful, but I'm a little disappointed at how hard it is to get some concrete information on connecting to the internet from Ubuntu.

Through four previous posts, I've been directed to the eciadsl modem driver and have been able to confirm that it works with my exact modem (there's even a nice picture of my Dlink DSL-200 modem on the eciadsl site).

But I open the eciadsl....deb package in Ubuntu and get the error "Dependancy is not satisfiable: PPPoe"

That the package won't even open on a virgin install of Ubuntu seems (to me at least) to be a pretty basic sort of error. Is there something I need to configure first? After all, PPPoE is over ethernet (which is not USB).

I'm a complete novice with Ubuntu so I have absolutely no idea where to start. 

Can any one help?

](*,)

---

### Post by dbd on 2006-10-20
no idea if this will help, but you could try to install pppoe, use your software installer or the command:
> sudo apt-get install pppoe
from the terminal to install it. Then try the deb again.

Re your disappointment: Not really a very useful thread name, but you have a point, modem support is very important, we should get as many as possible working out of the box, because without the net its hard to fix problems. Maybe you could get involved and help improve it :)

---

### Post by CatKiller on 2006-10-20
You could try installing PPPoE: ```
sudo aptitude install pppoe
```> **PPP over Ethernet driver**
PPP over Ethernet (PPPoE) is a protocol used by
many ADSL Internet service providers. This package allows
you to connect to those PPPoE service providers.

EDIT: beaten to it... ;)

---

### Post by Delkster on 2006-10-20
Actually, eciadsl is available in Ubuntu's `universe' software repository. It's generally a good idea to install software from the Ubuntu repositories if the piece of software you're looking for is available there.

It requires the pppoe package, as you've found out, and pppoe is also in universe.

You'll need to enable the universe repository (it's not enabled by default since the software in that repository is not officially supported by Canonical, but it generally works well nevertheless). The instructions can be found in the Ubuntu wiki:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

After enabling the universe repository, open **System > Administration > Synaptic Package Manager**, search for "eciadsl" and install it.

---

### Post by PriceChild on 2006-10-20
Because you don't have the internet, you will need to search [http://packages.ubuntu.com](http://packages.ubuntu.com) and download them, then transfer them by disc to your ubuntu machine.

install with a:
```
sudo dpkg -i <<package name>>.deb
```

---

### Post by BigLebowski on 2006-10-20
I had a DSL-200... so i also couldn't get my net working but i went out and bought a router/modem and it works, money well spent.

---

### Post by pcawdron on 2006-10-21
Thanks guys... got pppoe installed, got the eciadsl install but... now I have no idea what to do next. I can set my uid, pwd, select modem, remove the dabusb and make a config file but what's after that? I must be just inches away from connecting to the internet but I'm missing the final step. 

How do I switch it on?

---

### Post by AndreyYe on 2006-12-26
> **pcawdron said:**
> Thanks guys... got pppoe installed, got the eciadsl install but... now I have no idea what to do next. I can set my uid, pwd, select modem, remove the dabusb and make a config file but what's after that? I must be just inches away from connecting to the internet but I'm missing the final step. 

How do I switch it on?

if simply:
#eciadsl-config-text
(or #eciadsl-config-tk for GUI config but you need tcl and tk installed)
#eciadsl-start
#ifconfig
(just to check that tap0 or tun0 is up)
then optional, if your provider use ppp over ethernet:
#adsl-setup
#adsl-start
(or #pppoe-start in last versions of pppoe)
(# means that commands from root - use sudo)

if you need step-by-step instructions there's a lot of manuals on the net

---

