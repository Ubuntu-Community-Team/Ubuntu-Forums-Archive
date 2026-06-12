---
title: "Gday.. help with p2p/torrents"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by drowner on 2006-04-15
Hi!

One thing is still bringing me back 2 windows... shareaza... its the only program i can p2p download with. The bittorrent prog does nothing.... i think its probably my router.

My adsl router is a Zyxel prestige 600. Anyone else had, and hopefully fixed this situation!

Thanks guyzzzzz youre all the best

(sucks up for karma ;))

---

### Post by drowner on 2006-04-16
Bump ^^

---

### Post by bionnaki on 2006-04-16
forward the proper ports on your router. this is nothing to do with ubuntu.

---

### Post by nalmeth on 2006-04-16
Do you have a firewall setup? It's rare that merely a router would block your p2p sharing, but totally possible. If you installed a firewall, it is likely either Firestarter or Guarddog. 
For torrents, if you have a decent PC, download automatix and let it install java and azureus for you. Azureus gives you ton's of info, and will help you sort out those problems.
In my experience, linux p2p has been worlds better than windows.
The gIFT network brings together the major p2p networks and lets you use them all simultaneously. Thats Kazaa (fasttrack) Gnutella (Limewire) Ares, and OpenFT to name the major ones.
Apollon is a great client for the gift network, but there are many others, all ranging with different features, ease of use and installation.
 
Give some more info on your problems and people will be able to help.

---

### Post by drowner on 2006-04-16
Well, I have Azureus in Windows, and it does nothing. Something about not being able to open the right ports. Maybe its windows firewall, but i have never intentionally installed a firewall.

---

### Post by nalmeth on 2006-04-16
You can open ports on your router by logging into it. From a web browser, enter it's IP address, and try to go from there. I don't have much first-hand experience with this, but this is probably the way to go.
You should be able to find the router's IP from a terminal in linux with:
ifconfig eth0
Try installing azureus on ubuntu with automatix (you'll need to install java too) and see what results you get.
Post any problems you run into

---

### Post by aduckie on 2006-04-16
If you find out that your router doesn't block the ports, there is a possibility your ISP blocks the certain ports.

---

### Post by xXx 0wn3d xXx on 2006-04-16
If you want P2P/bittorrent programs you can use automatix to install them. It also has alot of other cool stuff. I recommend checking it out.

---

### Post by BarFly on 2006-04-16
[http://192.168.1.1/](http://192.168.1.1/)  Try typing this into your browser.  It should bring up your router's configuration.  It will ask for a password.  I assume you did not change the password.  More than likely, you leave the user name blank and use "admin" as the password.  Open up the port you want to use for P2P from there.  If you have a wireless router, you should really secure it, unless you want people downloading kiddie porn on your connection.  I leave mine open, but am prepared to block anyone who abuses it.  This is not an OS problem--  if you don't have a port open, you have the same problem whether using Linux, Windows, or whatever.

---

### Post by drowner on 2006-04-17
[QUOTE=BarFly][http://192.168.1.1/](http://192.168.1.1/)  Try typing this into your browser.  It should bring up your router's configuration.  It will ask for a password.  I assume you did not change the password.  More than likely, you leave the user name blank and use "admin" as the password.  Open up the port you want to use for P2P from there.  If you have a wireless router, you should really secure it, unless you want people downloading kiddie porn on your connection.  I leave mine open, but am prepared to block anyone who abuses it.  This is not an OS problem--  if you don't have a port open, you have the same problem whether using Linux, Windows, or whatever.[/QUOTE]

That helps heaps, and makes perfect sense to me:D Ill try it tonight.. at work now.

I dont remember seeing port settings on my router page, but i probably didnt look properly

---

### Post by BarFly on 2006-04-17
Oh, you will also have to tell your bittorrent program which port to use once it is opened.

---

### Post by jorn on 2006-04-17
There is also this site:
[http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm)

Jorn

---

### Post by drowner on 2006-04-17
[QUOTE=jorn]There is also this site:
[http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm)

Jorn[/QUOTE]
yeah... saw that site... it mentioned that i need a Static IP address, which my ISP wont let me have, apparently..... but ill cross that bridge if i come to it!

---

### Post by Kimm on 2006-04-17
your ISP wount let you have a static IP?
isnt that up to you and your router...?

---

