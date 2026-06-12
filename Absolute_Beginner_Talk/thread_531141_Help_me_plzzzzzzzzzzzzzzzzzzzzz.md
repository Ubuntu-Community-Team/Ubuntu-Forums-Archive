---
title: "Help me plzzzzzzzzzzzzzzzzzzzzz"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by sandeep37 on 2007-08-21
I am using cable internet connection which i will plug into LAN port and i have IP ,SUBNET,gateway address . I gave this address in the networking by selecting static IP . I am able to connect to net through XP.I dont have any modem with me i will just plug the cable in the LAN port . I am using local cable connection . I also tried the following things . Some one plz helps me

---

### Post by raijinsetsu on 2007-08-21
First off, your eth0 (which should be your network connection to the internet) is set to a static IP. This means that you will only get a connection if your ISP(your cable company) has that IP registered to your address.
Typically, you need a cable modem to connect to cable internet. It translates signals on the cable(remember this cable also carries TV signals) to ethernet (cat-5/e cable).
One thing you could try, if you have your cable modem, is to turn off the cable modem, unplug the network from your computer, turn on the cable modem, wait for it to fully power-on, then, edit your /etc/network/interfaces file. Use the Gnome network manager or KDE Network manager to do it. You should set the network adapter to "DHCP" or "Obtain automatically from DHCP". I forget the exact setting because I'm not in front of my computer. Then you can plug your network cable into your computer.

I hope that helps.

---

### Post by laidback on 2007-08-21
I'm using Fesity Fawn, Ubuntu 7.04, and although my ISP uses static addresses Feisty configured itself with DHCP, it works well. I've also installed Feisty on a laptop with wireless, it works there too.
If you're not using 7.04 it might be an idea to consider an upgrade.

---

### Post by ddrichardson on 2007-08-21
could you expand on how you connect the physical hardware?

Also try, if everything is set up as it would be in windows, disabling lPV6. This is enabled by default in Ubuntu and often causes problems.

---

