---
title: "New to xubuntu, couple of questions"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by MrZammler on 2007-01-29
Hi,

I've just installed xubuntu latest on my vaio P3 laptop, and I've got some questions:

I've setup my wireless card and connection, but each time I boot, I need to define the channel each time. In /etc/network/interfaces I've added a "wireless-channel 2" line, but it doesnt seem to make any difference. On each boot, I need to do a "sudo iwconfig eth1 channel 2" to get it to connect.

Second, since I have no permanent cdrom connected, I was wondering how to make it stop asking me to insert the cd when I want to install something, e.g. mplayer.

That's for now ;-)

Thanks

---

### Post by Pobega on 2007-01-29
> **MrZammler said:**
> Hi,

I've just installed xubuntu latest on my vaio P3 laptop, and I've got some questions:

I've setup my wireless card and connection, but each time I boot, I need to define the channel each time. In /etc/network/interfaces I've added a "wireless-channel 2" line, but it doesnt seem to make any difference. On each boot, I need to do a "sudo iwconfig eth1 channel 2" to get it to connect.

Second, since I have no permanent cdrom connected, I was wondering how to make it stop asking me to insert the cd when I want to install something, e.g. mplayer.

That's for now ;-)

Thanks

1) Download network-manager-gnome, and put it in your autostarted applications as nm-applet --sm-disable.

2) Edit the CD repos out of your /etc/apt/sources.list file, or just comment them out (Put a # before the line). Uncomment the universal edgy repos if they're commented. I'm not on Ubuntu right now so I can't check *exactly* what to do, but you should be able to figure it out.

---

