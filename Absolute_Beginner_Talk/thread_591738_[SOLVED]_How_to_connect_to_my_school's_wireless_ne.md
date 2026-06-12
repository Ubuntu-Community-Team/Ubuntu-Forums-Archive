---
title: "[SOLVED] How to connect to my school's wireless network?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-10-25
First off, let me say that like most of the free world, my school only provides support and has documentation for mac and windows computers. I hope to change this (and will probably only be able to when a linux itunes comes out), but in the meantime, I am the most qualified person on campus to work this out.

The school provides instructions for XP, vista, and macs. I have linked to them below (as pdfs), as they are too big to upload. The instructions vary, but here are some of the common threads:

1) PEAP authentication with a username and password (which I have)
2) Security type: 802.1x
3) Encryption type: WEP
4) The network uses certificate authentication
5) Network key will be automatically provided
6) Something about EAP-MISCHAP v2

I have no clue how to set this up in the network manager, so any help would be greatly obliged. 

The instructions are linked to below:
[http://www.bestsharing.com/files/Jt5PnF354246/wirelessPC.pdf.html](http://www.bestsharing.com/files/Jt5PnF354246/wirelessPC.pdf.html)
[http://www.bestsharing.com/files/MgrLPeQ354245/wirelessMAC.pdf.html](http://www.bestsharing.com/files/MgrLPeQ354245/wirelessMAC.pdf.html)
[http://www.bestsharing.com/files/xwTrWs354244/wirelessVISTA.pdf.html](http://www.bestsharing.com/files/xwTrWs354244/wirelessVISTA.pdf.html)

---

### Post by tonyyarusso on 2007-10-25
I'm not entirely familiar with it, but I can tell you this:  PEAP authentication was not very well supported before and was hard to configure, but as of Gutsy it is included by default, and network-manager should be able to do this just about automatically if you upgrade to Gutsy.  As far as the certificate, I'm not sure how that will be configured - maybe through Firefox?

---

### Post by rorestuff on 2007-10-25
Install nm-applet:

```
sudo aptitude install network-manager-gnome
```

Here's the link: [http://www.gnome.org/projects/NetworkManager/users/](http://www.gnome.org/projects/NetworkManager/users/)

It manages your wireless for you..

---

### Post by rouge568 on 2007-10-25
I have network manager installed, but I am not sure how to configure it manually for this - it will not automatically connect or prompt for password

---

### Post by rouge568 on 2008-03-27
update:
I talked to a fellow ubuntu-er at my school who had written a script to do this. Works great.

---

