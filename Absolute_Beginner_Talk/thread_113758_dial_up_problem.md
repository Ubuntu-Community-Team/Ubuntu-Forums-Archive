---
title: "dial up problem"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-01-07
:confused: :confused: :confused: i established a dial up connection as told in the support document.
it gets me connected to the isp but when i open a site in firefox it says no network connection present.
same with the GAIM messenger.
can anybody help.:confused: :confused: :confused:

---

### Post by rubinstein on 2006-01-07
Did you add a panel applet or did you configure it with System > ... > Network?

There is another option to connect with a modem: run
"sudo pppconfig" and configure the connection, then to connect run "sudo pon", to unconnect run "sudo poff". You can configure it to run under normal user, but better to get it working first under root and then we will see :-)

---

### Post by FireFighter on 2006-01-21
I need some help with the same problem. Yes, I did use network to configure the dial up setting, and when I open firefox, it says that it the page is unavailable. (not just one page but all pages). Completely new to Gnome. Couldn't find KPPP.:confused:

---

### Post by eriefisher on 2006-01-28
I just posted this very problem and then found this thread. sorry I'm new. I found the only way to get a connection is to disable eth0. The modem will dial and connect but you will not be able to communicate with eth0 active. I had the same problem while I was using MEPIS, this is what brought me to try Ubuntu. However the same problem still exist. Any direction in this matter would greatly appreciated.

Also is there any way to dial out without using passwords, this is a little extreme.

Thanks, eriefisher

---

