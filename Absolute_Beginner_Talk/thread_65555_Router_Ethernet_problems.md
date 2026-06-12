---
title: "Router/ Ethernet problems"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by kel on 2005-09-14
Hi all, I installed Breezy Badger the other day and all seemed to go well, except I can't connect to the internet through my router.

I used the network setup options to activate my Ethernet and I selected the DHCP option. The router (netgear - USB Modem/Ethernet combo) has one of those webpage setup windows where you type the ip then access the setup screen, I can use firefox to access the setup stuff on the router but I can't access the internet, but according to the router I am connected to the internet.

I've used the router with both a mac and PC as its set up now and it works fine with both of them. So I haven't got a clue what I need to be doing here, anyone got any suggestions?

Btw, if its any use, if enter [http://64.233.161.104](http://64.233.161.104) in firefox google does appear but external links don't work and if I type [www.google.com](www.google.com) firefox does nothing.

Thanks all.

---

### Post by xaverx on 2005-09-14
[QUOTE=kel]Hi all, I installed Breezy Badger the other day and all seemed to go well, except I can't connect to the internet through my router.

I used the network setup options to activate my Ethernet and I selected the DHCP option. The router (netgear - USB Modem/Ethernet combo) has one of those webpage setup windows where you type the ip then access the setup screen, I can use firefox to access the setup stuff on the router but I can't access the internet, but according to the router I am connected to the internet.

I've used the router with both a mac and PC as its set up now and it works fine with both of them. So I haven't got a clue what I need to be doing here, anyone got any suggestions?

Btw, if its any use, if enter [http://64.233.161.104](http://64.233.161.104) in firefox google does appear but external links don't work and if I type [www.google.com](www.google.com) firefox does nothing.

Thanks all.[/QUOTE]

Check your DNS settings in /etc/resolv.conf
add ip adress of DNS - nameserver x.x.x.x

---

### Post by kel on 2005-09-14
[QUOTE=xaverx]Check your DNS settings in /etc/resolv.conf
add ip adress of DNS - nameserver x.x.x.x[/QUOTE]

Should have mentioned I'm a linux noob, and not very good with nextworky router stuff :D

Is resolv.conf a txt file I can open and edit?

---

### Post by davmac on 2005-09-14
Yes. try "sudo gedit /etc/resolv.conf"

---

### Post by UbuWu on 2005-09-14
Try what happens if you type 'sudo dhclient' from a terminal. Does it work after that?

---

### Post by xaverx on 2005-09-14
yes, is text config file. Run e.g gnome-terminal and type sudo gedit /etc/resolv.conf
Then add ip adress of DNS, thich you get from your ISP. e.g Nameserver 195.x.x.x
and save. That's all. Or you can use a graphical settings over system-config-network

---

### Post by kel on 2005-09-14
Thanks guys, sorted now. I entred the DNS address into the DNS tab on the Network Setting dialogue and it's working fine now. I originally tried to edit the resdv.conf but it wouldn't let me, said I don't have permisions to alter it. [edit] I can alter it through the terminal though, supose I best get use to this.

Its odd this though as I tried to alter the DNS in the tab yesterday but it would't work, I've done a reinstall today and it seems to be working now.

btw, the problam was the ip that was automatically entered as my DNS was the adress of my router, not my actual DNS, well I think thats what the problam was.

Thanks again, I can play with ubuntu now :D

---

### Post by kel on 2005-09-14
Ahh, one more problam. If i reboot my computer the the DNS gets switched back to the wrong one. So I have to re-enter my DNS addresses again, which could get a bit dull. 

Anyone know of a permanent fix for this?

Thanks again.

---

### Post by UbuWu on 2005-09-14
You seem to be experiencing the same problems I do. Please read this bugreport and if it is exactly the same problem you have, please leave some comments confirming it... [http://bugzilla.ubuntu.com/show_bug.cgi?id=15340](http://bugzilla.ubuntu.com/show_bug.cgi?id=15340)

btw. does 'sudo dhclient' work for you as well fixing the problem temporary?

---

### Post by kel on 2005-09-15
[QUOTE=UbuWu]You seem to be experiencing the same problems I do. Please read this bugreport and if it is exactly the same problem you have, please leave some comments confirming it... [http://bugzilla.ubuntu.com/show_bug.cgi?id=15340](http://bugzilla.ubuntu.com/show_bug.cgi?id=15340)

btw. does 'sudo dhclient' work for you as well fixing the problem temporary?[/QUOTE]

'sudo dhclient' doesn't solve the problem, i still have to enter the DNS manually after a reboot.

I'm not sure how to report a bug but i'll look into it.

Thanks

---

