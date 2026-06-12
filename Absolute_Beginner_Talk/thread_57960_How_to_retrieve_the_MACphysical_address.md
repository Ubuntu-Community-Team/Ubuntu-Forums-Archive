---
title: "How to retrieve the MAC/physical address?"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by Vinze on 2005-08-18
How to retrieve the MAC/physical address? Doesn't matter if in terminal or not. Gnome or KDE. Please help.

---

### Post by JoshWilson on 2005-08-18
[QUOTE=Vinze]How to retrieve the MAC/physical address? Doesn't matter if in terminal or not. Gnome or KDE. Please help.[/QUOTE]
 Type in the following command from a terminal session:

ifconfig -a

Then look for the following line:

eth0      Link encap:Ethernet  HWaddr 00:02:55:32:AA:92

The HWaddr is your MAC Address.

---

### Post by Vinze on 2005-08-18
[QUOTE=JoshWilson]Type in the following command from a terminal session:

ifconfig -a

Then look for the following line:

eth0      Link encap:Ethernet  HWaddr 00:02:55:32:AA:92

The HWaddr is your MAC Address.[/QUOTE]
 Thanks a lot!

---

### Post by JoshWilson on 2005-08-18
[QUOTE=Vinze]Thanks a lot![/QUOTE]
 No problem!  Please be sure to "Add to my reputation" using the button under my name that looks like a green check mark and a red X.

Thanks a bunch!

You could even go a step further and type:

ifconfig -a |grep -i hwaddr

And it will list all of the Mac Addresses for each valid network adapter.  Kind of cleans up the mess a bit so you don't have to sift through so much output.

---

### Post by Vinze on 2005-08-19
[QUOTE=JoshWilson]No problem!  Please be sure to "Add to my reputation" using the button under my name that looks like a green check mark and a red X.

Thanks a bunch!

You could even go a step further and type:

ifconfig -a |grep -i hwaddr

And it will list all of the Mac Addresses for each valid network adapter.  Kind of cleans up the mess a bit so you don't have to sift through so much output.[/QUOTE]

LOL, had done that already  :wink: 

But I have a wireless connection, I suppose I have to take the one after > wlan0     Link encap:Ethernet HWaddr?

---

