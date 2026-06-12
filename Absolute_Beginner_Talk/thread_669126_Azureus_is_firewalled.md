---
title: "Azureus is firewalled"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by G. Cotgreave on 2008-01-16
I installed azureus while i was living in Denmark were i was geting internet from the university i was studying so i knew that the ports for downloading torrents were closed but now that i returned to my country (Greece) i still get the NAT Firewalled message and the NAT Test is failing...any suggestions? 
I use a Baudtec Wireless Modem router that i was given by my internet provider and it has been configured through the Win box that my sister has.

---

### Post by philinux on 2008-01-16
This has come a few times before. Azureus is buggy and a resource hog as it uses java. (Quote from the mods). It's also fiddly with routers. 

Get Deluge and your problems are gone. [http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by SOULRiDER on 2008-01-16
To check your firewall settings in Ubuntu you can install Firestarter
```
sudo aptitude install firestarter
```
If you use Kubuntu you probably want Guarddog
```
sudo aptitude install guarddog
```
Use one of these programs to check your firewall.

You may also want to check your routers configuration and make sure it doesnt have a firewall active or that it isnt blocking the ports youre using.

---

### Post by SOULRiDER on 2008-01-16
> **philinux said:**
> This has come a few times before. Azureus is buggy and a resource hog as it uses java. (Quote from the mods). It's also fiddly with routers. 

Get Deluge and your problems are gone. [http://deluge-torrent.org/](http://deluge-torrent.org/)

That works too, and is probably a much better alternative :)

---

### Post by AndyCooll on 2008-01-16
There are a number of possibilities you can try in Azureus. 
-You can try setting it to use UPnP if it isn't already.
-You can manually change the port it uses to one you know will work. 
-You could even try port forwarding on the router a particular port to your machine.

:cool:

---

### Post by frodon on 2008-01-16
If you have a router make sure you forwarded the good port(s) to your computer, without this no bittorent client will be able to connect correctly, this is an inescapable step with a NAT router.

---

### Post by AndyCooll on 2008-01-16
> **philinux said:**
> This has come a few times before. Azureus is buggy and a resource hog as it uses java. (Quote from the mods). It's also fiddly with routers. 

Get Deluge and your problems are gone. [http://deluge-torrent.org/](http://deluge-torrent.org/)

Depends on who you ask and who uses it. I used it for ages and it worked great. Absolutely no problems with the router. It can use UPnP and use ports dynamically.
I've had far more problems getting Deluge to run successfully (and I like that too).

IMHO this is not the answer the OP is seeking. Just as if you have a problem when using Deluge, you're not seeking an answer "change to Azureus instead". There's a time and place to advertise the benefits of Deluge, this isn't it.

:cool:

---

