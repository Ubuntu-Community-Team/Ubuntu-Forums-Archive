---
title: "No LAN connection on any Ubuntu machine"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by woodi100 on 2008-02-13
Hi everyone,

I have been unable to find a fix for this problem, but please feel free to point me at it.

basically, when I install Ubuntu 7.10 on any of my computers, I cannot get on my network at home. The machines are variously Fujitsu Siemens, dell etc. I can configure  between DHCP and fixed IP etc, but still can't get anything at all, now LAN, internet etc.

I've now taken to testing it with a Live CD on lots of other PCs that I can gain access to, and seem to have the problem all the time.

LAN is Cat5 with a D-Link ADSL Router, network cards are non-brand RTL etc, a few 3Com etc.

Many thanks for any pointers to a solution.

Graham

---

### Post by LRT on 2008-02-13
can you get connection on ANY of your computers on the lan??? if you can't this may be a router problem... try connecting a computer straight from the modem, bypassing the router...

---

### Post by woodi100 on 2008-02-14
Yes, Windows PCs and Apple Macs can connect with no problem at all, as can a PC bootted with Ubuntu 6.10 Live CD. It's just the Ubuntu 7.10 that's the persistent problem :(

---

### Post by sigge on 2008-02-14
Try blacklisting IPV6. I have heard people have problems with this....
:(
EDIT: I'm not shure how to do this, so I hope someone else follows up with a link or howto... :)

---

### Post by LRT on 2008-02-14
could you post the contents of your /etc/network/interfaces file and the output of ifconfig command...

---

### Post by dca on 2008-02-14
...also you can try accessing network card(s) through 'System -> Administration -> Network' on the menu panels.  Make sure network card has check amrk on 'enable roaming mode' and if DHCP is set to automatic.  Go to DNS tab and clear out anything in there and restart system versus restarting only network services....

---

### Post by woodi100 on 2008-02-14
Thanks everyone, I will try these things this evening. Just as an interesting aside, I downloaded the KDE version and had no problems with the Live CD at all, networking just worked right out of the box.

---

### Post by KCormier on 2008-02-14
Is this with the same cd?  Could be a corrupt download/burn...  When you have one problem that happens across many computers but not for everyone else it's usually a media related issue... :-D

---

### Post by woodi100 on 2008-02-14
Different CD, it's the Kubuntu disc that has the KDE, not the Ubuntu (Gnome) disk.

It's definitely not media related, I've a download version and the Ubuntu-pressed version :(

Going to have a last play now...

---

