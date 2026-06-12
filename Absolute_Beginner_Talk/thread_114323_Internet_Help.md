---
title: "Internet Help"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by Josh1 on 2006-01-08
I have a 'Motorola SB5100 SURFBoard Cable Modem' , running perfect 100% on Windows XP. (Using USB at the moment).
I have a few spare Ethernet cards around (2+), with one inbuilt into pc.
Now, how do i configure the internet with ubuntu linux? Im good at guessing, and that usually gets me places with most things in life, and i have got to the network settings.
So, i choose DHCP and it goes active, add my DNS servers (from ipconfig /all with windows xp), etc but it still wont work.
Can someone explain how to setup the net, or a guide?
Thanks,
- Josh

---

### Post by Greg2 on 2006-01-08
[QUOTE=Josh1]I have a 'Motorola SB5100 SURFBoard Cable Modem' , running perfect 100% on Windows XP. (Using USB at the moment).
I have a few spare Ethernet cards around (2+), with one inbuilt into pc.
Now, how do i configure the internet with ubuntu linux? Im good at guessing, and that usually gets me places with most things in life, and i have got to the network settings.
So, i choose DHCP and it goes active, add my DNS servers (from ipconfig /all with windows xp), etc but it still wont work.[/QUOTE]
Are you using a crossover cable? You need to use crossover cable for peer to peer, so you can share your internet connection.

---

### Post by lukem on 2006-01-08
More experienced users might have an easier way, but I work with cable modems and I would suggest that you turn off your PC and modem.  If you are using a router turn it off also.  Power on the 5100 and wait for it to lock on to the upstream and downstream cable signals.  I think there is one cable light on the 5100 and it should be lit steady.  Then power on your router and wait for it to stabalize.  Then boot your pc and it should get an address and all will be well.

Luke

---

### Post by Josh1 on 2006-01-08
[QUOTE=lukem]More experienced users might have an easier way, but I work with cable modems and I would suggest that you turn off your PC and modem.  If you are using a router turn it off also.  Power on the 5100 and wait for it to lock on to the upstream and downstream cable signals.  I think there is one cable light on the 5100 and it should be lit steady.  Then power on your router and wait for it to stabalize.  Then boot your pc and it should get an address and all will be well.

Luke[/QUOTE]
No router.
Ok, ill try this, thanks for your help lukem :)

And its the modem as well i think. :) (edit: the cords, are for the modem)

---

### Post by mips on 2006-01-08
Josh1,

I know with some cable/ISP providers you need to register each PC's MAC address with their online registration system.

If you are still having hassles let us know who your ISP is with a weblink to the service you are using. Usually by looking at the windows guides it is relatively easy to figure out what needs to be done in Linux.

---

### Post by Josh1 on 2006-01-09
[QUOTE=mips]Josh1,

I know with some cable/ISP providers you need to register each PC's MAC address with their online registration system.

If you are still having hassles let us know who your ISP is with a weblink to the service you are using. Usually by looking at the windows guides it is relatively easy to figure out what needs to be done in Linux.[/QUOTE]
[www.e-wire.net.au](www.e-wire.net.au)

Ill give ISP a ring when i get home.
Thanks guys :D

---

### Post by mips on 2006-01-10
Ok, the MAC address thing does not apply to you. Mostly people form the states.

Do you live in one of the following areas:
Dalyellup, Maylands, Princeton/Roslea or Mandurah ?

Try changing your MTU values to 1200 and if you are a Cruise client to 1100.

[http://www.e-wire.net.au/support/notices.php](http://www.e-wire.net.au/support/notices.php)

Look here to see how to change our MTU values, [http://ubuntuforums.org/showthread.php?t=82093](http://ubuntuforums.org/showthread.php?t=82093)

If you still have no luck then:
Paste the contents of **/etc/resolv.conf** & **/etc/network/interfaces** here.
Paste the output of the following commands here, 
[B]ifconfig eth0
route -n[/B]

Also try disabling IPv6.

[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

