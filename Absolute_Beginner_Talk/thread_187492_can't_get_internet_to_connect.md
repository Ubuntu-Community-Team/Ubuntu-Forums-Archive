---
title: "can't get internet to connect"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by cmt on 2006-06-03
help,
i can't seem to get ubuntu to hook up to the net, my other 2 computers are fine, so i know its live.  is there anything you need to do to config it to hook up to the net?
and, being such a noob, how do you access the shell?

---

### Post by Trab on 2006-06-03
the shell (if you are running gnome) is in applications/accessories/terminal

ummmm no, nothing special, its just a direct ethernet connection?
once in the terminal, try pinging a few things, see wat it says.
also, check out system/administartion/networking in case for some odd reason you need to enable your card.

as far as i remember, you have to have an internet connection on ubuntu in order to even install the thing! it downloads the majority of its packages, hense why it only has 1 install CD.

---

### Post by cmt on 2006-06-03
well, since it wasn't hooked up to the internet when i installed the cd, that might be the reason that its not working...whats the easiest way to reinstall it?

---

### Post by XAsmodeanX on 2006-06-03
You don't need to reinstall.  There are a few things that you need to try.  If you are using regular ethernet to connect to the internet, you'll want to verify that you have your ethernet interface up.

Open a terminal, and type in 'ifconfig eth1' without the ''.  If the output of that command sais "connected" then try this:  'sudo dhclient' again without the ''s.  If you still don't have internet try this:  'ifconfig eth1 down' then type in 'ifconfig eth1 up'.  If none of that works, go into the /etc/ folder in your root directories and edit the file "resolv.conf".  Take a look at the file and if there is a ip address that is your router, erase that line completely.

---

