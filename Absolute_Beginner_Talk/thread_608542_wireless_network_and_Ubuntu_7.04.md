---
title: "wireless network and Ubuntu 7.04"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Tom_YU on 2007-11-10
Hole day I am trying to set my wireless network and I can't do it...I have
TP-LINK 11b/g wireless adapter
If anyone knows how to do it?

---

### Post by gigaferz on 2007-11-10
you could tell us what you've done so far, 

  i didnt search about your adapter, but 
[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)
 could help you...
people will ask you to post thie output of
sudo lshw
and
dmesg

on the terminal applications-> accsesories->terminal
get ready...

---

### Post by Tom_YU on 2007-11-10
My friend helped me to this:

______________________

ifconfig etho (my IP adress)

route add default

ifconfig eth0 up

_______________

I am totaly beginner at linux and I am reallu need help...

---

### Post by gigaferz on 2007-11-10
did you find the terminal?

read my post above.

type in there (or copu and paste ) this

sudo lshw

it will ask you for a password just type it and press enter (you will not see any characters showing)

---

