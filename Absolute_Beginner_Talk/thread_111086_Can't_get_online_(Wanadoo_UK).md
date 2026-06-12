---
title: "Can't get online (Wanadoo UK)"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by zongamin on 2006-01-01
I've just installed ubuntu on my laptop and I can't get online either wireless or via the ethernet cable.

The wireless adapater is a USB inventel - ubuntu doesn't seem to recognise it all - any ideas how I can get it to recognise?

Or does anyone know what I need to enter into the Network settings box to get the ethernet connection to work?

Thanks,

---

### Post by d1337 on 2006-01-01
Not familiar with your wireless card, but your wired connection is likely the best start anyway.  I'm assuming that you are behind a router.  Do you know how the router is set up, mostly regarding it's IP Address & is it set up to allow DHCP connections and assign IP addresses?  Were you connected to your wired connection during install?

d1337

---

### Post by zongamin on 2006-01-02
[QUOTE=d1337]Not familiar with your wireless card, but your wired connection is likely the best start anyway.  I'm assuming that you are behind a router.  Do you know how the router is set up, mostly regarding it's IP Address & is it set up to allow DHCP connections and assign IP addresses?  Were you connected to your wired connection during install?

d1337[/QUOTE]

The router is wanadoo's Livebox - made by Inventel also.

I wasn't connected to it during install - is it worth me installing again with it connected?

---

### Post by d1337 on 2006-01-02
Shouldn't be necessary to reinstall while connected.  Do you know the ip address of the router?  Are you familiar with command line?  If so, could you post your /etc/network/interfaces file for me here (wrap code tags around it please).

If you are not familiar with command line, I'll do my best to direct you.  Open a terminal: Applications-->Accessories-->Terminal

Issue this command:
```
sudo cat /etc/network/interfaces
```
Highlight the text from that file (all of it) and copy/paste into a reply to this thread (after highlighting, middle click is a nifty shortcut to paste it where you want it).  In the reply, highlight the text and select the "#" sign on the toolbar to wrap code tags around it (makes it easier to navigate for folks that want to help you).  If you have problems, I'll be watching this thread and I'll help best I can.

d1337

EDIT...Not enough coffee yet this AM.  It'll be difficult to post your file as I requested if you aren't able to connect to the internet.  You could, however, copy it in to a text file, save to diskette or stick and take it to another box that is on the net.  Sorry, I'm just a bit groggy yet from New Years.

---

### Post by zongamin on 2006-01-03
[QUOTE=d1337]Shouldn't be necessary to reinstall while connected.  Do you know the ip address of the router?  Are you familiar with command line?  If so, could you post your /etc/network/interfaces file for me here (wrap code tags around it please).

If you are not familiar with command line, I'll do my best to direct you.  Open a terminal: Applications-->Accessories-->Terminal

Issue this command:
```
sudo cat /etc/network/interfaces
```
Highlight the text from that file (all of it) and copy/paste into a reply to this thread (after highlighting, middle click is a nifty shortcut to paste it where you want it).  In the reply, highlight the text and select the "#" sign on the toolbar to wrap code tags around it (makes it easier to navigate for folks that want to help you).  If you have problems, I'll be watching this thread and I'll help best I can.

d1337

EDIT...Not enough coffee yet this AM.  It'll be difficult to post your file as I requested if you aren't able to connect to the internet.  You could, however, copy it in to a text file, save to diskette or stick and take it to another box that is on the net.  Sorry, I'm just a bit groggy yet from New Years.[/QUOTE]


Thanks - I wil try this when I get home (am working at moment) - and I will post a reply as soon as I can.

Many thanks for the help,

---

