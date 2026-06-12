---
title: "Grumpy network"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-03-26
Hi,

I've got two computers at home. My wife uses and XP machine in the loft, connected to the network wirelessly, (Belkin)

I've got a new machine :O)
Duel boot, Ubuntu and XP.

XP connects to the network perfectly.
Ubuntu also.................sometimes.

Sometimes I log on and everything works.
Other times, I simply can't see the other computer, any of its files, or use its printer.
Sometimes a shut-down, start-up fixes it, sometimes it doesn't

Is there a way to re-detect the network after the computer has started up?


Philhttp://ubuntuforums.org/images/smilies/eusa_boohoo.gif

---

### Post by jhenager on 2007-03-26
Ubuntu Linux users use sudo command with Debian Linux command:
# sudo /etc/init.d/networking restart

To start Linux network service:
# sudo /etc/init.d/networking start

To stop Linux network service:
# sudo /etc/init.d/networking stop

---

### Post by groeswenphil on 2007-03-26
Well, tried all those and nothing happened at all.

Am I doing this right?

I click PLACES>CONNECT TO SERVER>
I pick service type, WINDOWS SHARE

I type in the name of my home network where it says Server:
Then, whether I click BROWSE or Connect, it shows me an icon with my home network name. If I click on it,  it thinks for a while then up pops a window saying, "The folder contents could not be displayed"

I would have thought that clicking on the icon with my home network's name would bring up icons for the computers on my network, which it does sometimes, but not always.

The system is firewalled at the router and I have set sharing permissions on the XP computer.

Thanks for the help,
Phil Edwards

---

