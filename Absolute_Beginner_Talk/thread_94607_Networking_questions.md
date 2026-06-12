---
title: "Networking questions"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by inha on 2005-11-24
So I've got this brand new laptop sitting besides by desktop computer now and I was wondering what would be the best way to arrange communication between the two of them. I've got a spare ethernet card and a few meters of rj-45 which I guess I could use to set up a home network. Or could I just connect the two via an usb cable? My adsl modem has multiple ports so I wouldn't have to set up so much stuff if I just connected the two via usb and used "separate" internet connections. Or atleast I think so based on my nonexistant networking knowledge.

---

### Post by apjone on 2005-11-24
1. connect your desktop to the adsl modem to access the net
2. Is the rj45 a cross over cable? if so connect them together via ethernet
3. Set a static IP to your desktop and laptop
4. Set your laptop up to use the desktops IP as its Default gateway
5. Check the desktops firewall setting to make sure that the connection is allowed
6. Add your DNS address to the laptops connection details

---

### Post by wjp.reg on 2005-11-24
[QUOTE=inha]So I've got this brand new laptop sitting besides by desktop computer now and I was wondering what would be the best way to arrange communication between the two of them. I've got a spare ethernet card and a few meters of rj-45 which I guess I could use to set up a home network. Or could I just connect the two via an usb cable? My adsl modem has multiple ports so I wouldn't have to set up so much stuff if I just connected the two via usb and used "separate" internet connections. Or atleast I think so based on my nonexistant networking knowledge.[/QUOTE]

```
what would be the best way to arrange communication between the two of them
```

Depends; what OS are you running on the laptop / desktop ?

What kind of nic is available in each computer; I assume you have ethernet in the desktop; what about the laptop?

```
 My adsl modem has multiple ports so I wouldn't have to set up so much stuff if I just connected the two via usb and used "separate" internet connections.
```

What about a firewall?

Why not spend a few bucks and get a router to hide behind?

That could solve your network connection problem as well.

Or, you could setup the desktop for internet sharing and have that system be the firewall.

some things to think about..

Any one else?

---

### Post by inha on 2005-11-24
[QUOTE=apjone]1. connect your desktop to the adsl modem to access the net
2. Is the rj45 a cross over cable? if so connect them together via ethernet
3. Set a static IP to your desktop and laptop
4. Set your laptop up to use the desktops IP as its Default gateway
5. Check the desktops firewall setting to make sure that the connection is allowed
6. Add your DNS address to the laptops connection details[/QUOTE]

3. is giving me doubts. I'm connected to the internet via DHCP.

---

### Post by inha on 2005-11-24
Scratch my last post. 

So I plugged in the ethernet card and connected the computers. I set my desktops second ethernet to have an ip 192.168.1.1 and the laptops 192.168.1.2 and the laptop's gateway to be the desktop's ip. The dns info was already there for the laptop, probably because I had already connected it to the internet with it. I don't have a firewall on my desktop but yet the laptop can't see the desktop. Nor can the desktop see the laptop. 

What to do now?

---

