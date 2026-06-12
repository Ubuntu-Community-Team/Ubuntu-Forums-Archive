---
title: "New to Ubuntu, getting started"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by MG Sailor on 2007-01-25
As the title says I installed Ubuntu the day before. It's all new to me and I am c-o-m-p-l-e-t-e-l-y lost.

1) When I boot I get the OS options and in 10 secs it boots in the default, which is Linux. No prob with me but little sister needs (pfff, likes) XP. How can I make the Win partition my primary partition so that it will boot in XP unless I choose otherwise?

2) Any help on the commands would be appreciated. Of course you couldn't list them here but a link to a manual or something would be great.

3) Last but not least, how can  I connect to the net? I found something like ''connect to internet service'' but dunno how to configure it to use my ISP.

That's it for now. I'll post if anything else comes up. Thanks in advance.

---

### Post by xfceslacker on 2007-01-25
1. That menu you see is called GRUB. GRUB is a bootloader. To change the default OS. You need to edit the config file for grub. You can find it in /boot/grub/menu.lst. Open it with something like this:
```
sudo gedit /boot/grub/menu.lst
```

Then look for this:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
```

So just count how many down your windows is on the list, and follow the comments above
the "default 0" spot in the file. 

2. I found this link [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml). I'd search google too.

3. I don't know.

---

### Post by j19sch on 2007-01-25
> **MG Sailor said:**
> 3) Last but not least, how can  I connect to the net? I found something like ''connect to internet service'' but dunno how to configure it to use my ISP.
Have you tried just starting your browser and accessing a web page?
Often enough there is no need to configure anything.

Joep

---

### Post by bastiegast on 2007-01-25
Connecting to the internet depends on what you use. Do you have a dail-up moden? ADSL/Cable modem, are you behind a router(Is your computer in a small home network)? etc.

---

### Post by MG Sailor on 2007-01-25
Thanks about the help on booting and the link to the guide :).

One thing left. I have an ADSL connection. Phoned the ISP to ask about the type of the connection and they said it's a PPPoA. I'm not on a LAN, just one PC with a modem.
I opened FF of course but it said "Server not found" and the usual advice on checking the spelling and such. As far as I remember (I have to be on XP to post here) there must be something like a client under the "services" or "applications" menu but as I said before, I can't figure out how it works.

---

### Post by TheWizzard on 2007-01-25
> **MG Sailor said:**
> Thanks about the help on booting and the link to the guide :).

One thing left. I have an ADSL connection. Phoned the ISP to ask about the type of the connection and they said it's a PPPoA. I'm not on a LAN, just one PC with a modem.
I opened FF of course but it said "Server not found" and the usual advice on checking the spelling and such. As far as I remember (I have to be on XP to post here) there must be something like a client under the "services" or "applications" menu but as I said before, I can't figure out how it works.

the easy way is to buy a router. use the router to connect to your isp and you're done. 
without a router it's a bit more work. i used to connect like this a few years ago, but i forgot how to do this exactly. maybe this helps: 
[http://en.tldp.org/HOWTO/PPP-HOWTO/](http://en.tldp.org/HOWTO/PPP-HOWTO/) 

but again: the easy way is to buy yourself a router.

---

### Post by MG Sailor on 2007-01-25
Problem! I opened the terminal and typed "sudo gedit /boot/grub/menu.lst" to configure the boot sequence but it says "command not found". Is something wrong? Note that it's GNU Grub v 0.96.

As for the connection, buying a router is not what I had in mind ($$$ needed for that). I opened the network settings and there displayed was my 56 k modem which is in the case. I tried to auto detect the Sagem DSL modem with no luck. How can I manually find it?

---

### Post by jvc26 on 2007-01-25
What version of Ubuntu have you installed?
Btw, that command should be:
```

gksudo gedit /boot/grub/menu.lst

```
As for graphical apps like gedit you should always use gksudo rather than sudo (thats not an accusation at you, merely a pointer for the future and for the poster of the above instructions) if you want more info read: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)
however, that command should work, not sure why its saying command not found.
Another possibility is to try the text editor within the terminal:
```

sudo nano /boot/grub/menu.lst

```
And see what that puts back.

EDIT:: Apologies to TheWizzard I edited my post to add the nano suggestion before I saw your reply.
Il

---

### Post by TheWizzard on 2007-01-25
> **MG Sailor said:**
> Problem! I opened the terminal and typed "sudo gedit /boot/grub/menu.lst" to configure the boot sequence but it says "command not found". Is something wrong? 

try 
```
sudo nano /boot/grub/menu.lst
```

> **MG Sailor said:**
> As for the connection, buying a router is not what I had in mind ($$$ needed for that). I opened the network settings and there displayed was my 56 k modem which is in the case. I tried to auto detect the Sagem DSL modem with no luck. How can I manually find it?

you can afford dsl but not a router? routers are quite cheap compared to the monthly contribution for dsl. 

is your modem ethernet or usb? if it's ethernet, you'll need to use eth0. 
pppoeconf and pppconfig are installed by default. but i think the quickest fix for you is to search this forum. there are quite a lot of treads about this topic.

---

### Post by MG Sailor on 2007-01-28
I configured the boot loader to have XP as default, thanks for the help.
> you can afford dsl but not a routerI'm a teenager so 25 Euros a month is already much :p. 
I have a USB modem.  If there are other threads about it I will find them. 
I guess all questions are answered now. Thank you and... see you!

---

### Post by TheWizzard on 2007-01-28
> **MG Sailor said:**
> I configured the boot loader to have XP as default, thanks for the help.
I'm a teenager so 25 Euros a month is already much :p. 
I have a USB modem.  If there are other threads about it I will find them. 
I guess all questions are answered now. Thank you and... see you!

ok, good luck!

---

