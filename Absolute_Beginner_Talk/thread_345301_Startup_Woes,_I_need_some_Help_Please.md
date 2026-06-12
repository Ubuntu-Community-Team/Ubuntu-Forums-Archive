---
title: "Startup Woes, I need some Help Please"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Jeff D on 2007-01-24
Hi all I've been using Ubuntu now for quite a while now and have managed to overcome pretty much any quirks Ubuntu has thrown at me by reading the posts thanks to the knowlegable folk on here.  My problem that has me stumped is as follows:  I allowed some updates tonight load and shortly thereafter my net connection slowed down followed by the computer slowing down so I figured a reboot was in order for the updates.  After the restart it hanged a little longer on boot-up then normal but finally got to the log-in screen.  Punched in my username/pass and it started hanging again on the brown background of Ubuntu for about 5 minutes then popped up this error:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

  After this I can browse around and connect to the net but am unable to run the sudo command or update/install.  So does anyone have any background on this error or know of any way to get things back to normal?  Thanks in advance for any replies as I truly don't want to have to reinstall after getting everything running perfect after many months of trial and error.

---

### Post by swamytk on 2007-01-24
Please ensure that HAL, DBUS services are started successfully and running properly.

---

### Post by Jeff D on 2007-01-24
> **swamytk said:**
> Please ensure that HAL, DBUS services are started successfully and running properly.

  Thanks very much for your reply.  As a relative newbie to Ubuntu how might I go about doing this?

---

### Post by Jeff D on 2007-01-24
Hmm figured it out.  Seemed to be a conflict in my /etc/network/interfaces that was making the start up wonky.  Redid the interfaces file and all seems normal again. :D

---

### Post by NewDisciple on 2007-01-24
Could you please explain what you changed in your interface?  I'm having the same problem, which started last night.
Here is my /etc/network/interfaces list:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

I'm thinking that this is related to a update (have no idea which one).  I even reinstalled but still had the same problem after updating.  Would appreciate any guidance.

---

### Post by swamytk on 2007-01-25
> **NewDisciple said:**
> Could you please explain what you changed in your interface?  I'm having the same problem, which started last night.
Here is my /etc/network/interfaces list:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

I'm thinking that this is related to a update (have no idea which one).  I even reinstalled but still had the same problem after updating.  Would appreciate any guidance.

Remove the unnecessary interfaces. For example if you have ethernet card as eth0, remove all other eth*, ath*, wlan* sections, except lo.

---

