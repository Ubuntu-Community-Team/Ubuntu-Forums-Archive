---
title: "WTF ubuntu randomly removing icons"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Evil Wayz on 2007-11-20
[IMG]http://www.debianadmin.com/images/wpa/2.png[/IMG]

This is what my statusbar used to look like.

Now, the voluem control dissappeared adn was replaced by controls for the modem and pc speaker.

Solved that by rebooting.

Still have no wireless bars.  Still have no battery charge indicator.   This all happpened when my comp crashed the other day.

Any ideas how to get this stuff back? i tried added it to the panel but the features arent working, they dont appear to be hte same as the old programs.

Also my update manager icon doesnt pop up when there is new stuff to install. I have about had it with ******* Ubuntu.

---

### Post by HermanAB on 2007-11-20
On Ubuntu, you have to lock the panel widgets to keep them from getting periodically screwed up.

The easiest way to fix things is to create a new user account and copy your data over.   Then you have to edit /etc/sudoers to give your new user root access.  There are other ways, but this is the easiest one.

---

### Post by philinux on 2007-11-20
Sounds like you need to add to panel, scroll right down and find notification area. This is whats missing by the sound of it.

---

### Post by Inxsible on 2007-11-20
> **philinux said:**
> Sounds like you need to add to panel, scroll right down and find notification area. This is whats missing by the sound of it.
I don't think thats it. He is missing only a few icons from the notification area, not all. :(

---

### Post by Evil Wayz on 2007-11-20
> **HermanAB said:**
> On Ubuntu, you have to lock the panel widgets to keep them from getting periodically screwed up.

The easiest way to fix things is to create a new user account and copy your data over.   Then you have to edit /etc/sudoers to give your new user root access.  There are other ways, but this is the easiest one.

> **Inxsible said:**
> I don't think thats it. He is missing only a few icons from the notification area, not all. :(

They were locked. And that volume thing almost caused me to launch my laptop into the stratosphere.

I would really like the ability to select networks and maybe get an icon to tell me updates are available. And if i have to reinstall ubuntu one more time i'm switching to freakin linux mint and washing my hands of it. 

I even tried unisntalling and reinstallign network manager. nothing.

EDIT:

Get this. I created a NEW panel, added a notification area to it and BOTH icons i wanted showed up. But when i add a notification area to the top taskbar, only the power one shows up. so I tried deleting the new taskbar, and now the wireless won't show up. what is UP with that.

---

### Post by Evil Wayz on 2007-11-20
also i created a new user, and guess what! i get wireless notification in that account but not my mine.

---

### Post by Inxsible on 2007-11-20
Maybe your configuration files got messed up. in that case you can do this.
```
killall nm-applet
```Then remove your config files from your home directory for network manager. look in two places ~/.gconfd and ~/.gconf

remove them and then restart nm-applet

---

