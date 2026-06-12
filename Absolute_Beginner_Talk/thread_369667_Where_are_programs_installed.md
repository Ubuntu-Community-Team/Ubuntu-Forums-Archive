---
title: "Where are programs installed?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by krunk on 2007-02-24
Hi, I finally got my internet connection working with ubuntu.. although it seems slower then when im on XP. But I used Synaptic to install Xchat, I can use the program.. but I want to know where the xhcat dir is, so i can install scripts and such. Where are programs installed? its not in my home dir or desktop. I typed cd xchat in the terminal but that wasn't a valid dir. any help please?

---

### Post by halitech on 2007-02-24
it should show up in the internet menu, you shouldn't need to do anything from the terminal

---

### Post by Maestro23 on 2007-02-24
> **krunk said:**
> Hi, I finally got my internet connection working with ubuntu.. although it seems slower then when im on XP. But I used Synaptic to install Xchat, I can use the program.. but I want to know where the xhcat dir is, so i can install scripts and such. Where are programs installed? its not in my home dir or desktop. I typed cd xchat in the terminal but that wasn't a valid dir. any help please?

Programs installed via Synaptic, apt-get, aptitude are stored in:

[COLOR="Red"]/usr/bin[/COLOR]

You will need this path to create a menu item or desktop launcher for the program. Although most programs installed by the above methods, automatically create a menu item.

Also can type from command line:

> which "program name"

---

### Post by krunk on 2007-02-24
ok thanks, But I think I may have accidentally installed 2 versions of Xchat, one says "Xchat IRC Client" and one says "Gnome Xchat IRC Client" ... when  I tried to remove the first one with add/remove progs. it says 'xchat is not available in any software channel' 'the application might not support your system architecture'

How can I uninstall this program so I can just have Gnome Xchat????

---

### Post by irish_flu on 2007-02-24
Hey buddy,  if your internet connection seems slower than Windows, you might try disabling IPv6 support.  That made mine seem faster, and many other folks too.

I followed the numbered instructions 1-4 in the first post on this page, then rebooted.  Boom, networking felt faster.
[http://ubuntuforums.org/showthread.php?t=6841&highlight=disable+ipv6](http://ubuntuforums.org/showthread.php?t=6841&highlight=disable+ipv6)

---

