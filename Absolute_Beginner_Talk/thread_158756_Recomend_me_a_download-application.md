---
title: "Recomend me a download-application"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by ubunutu_it_is on 2006-04-11
Hi!
I need to download some stuff and it is ofcourse that i need the best download application.
I've tried to download a bitturrent client, but it decided to not work :( (the linux version).

---

### Post by Sef on 2006-04-11
> I've tried to download a bitturrent client

A bittorrent client is included.   Applications > Internet > BitTorrent

If you want another one, go to Applications > Add Applications > Internet > more programs.  There are a couple of BitTorrent clients there:

---

### Post by edwina on 2006-04-11
Did you download BitTorrent via Synaptic? In what way does it not work? It may well be the best option for you, so it is worth trying to get it going.

---

### Post by nalmeth on 2006-04-11
You want p2p?
Some clients include:
apollon
frostwire
limewire
mldonkey (difficult to setup, but supports all major networks and torrents)


TORRENTS:
azureus (a little heavy on CPU, but impressive app)
bittorrent
bittornado
ktorrent

If you got a message saying couldn't connect to tracker, it doesn't necessarily mean that it's not working. You didn't mention what was going wrong.

---

### Post by hbush on 2006-04-11
OK I had the same problem, 
first I opened a port in firestarter, than to make sure it will work I opened the port on the linksys router as well. Now it works fine but please don't do this before consulting some expert regarding security question . (I am not sure if this is good or bad)

how: 
- Programs --> System Tools --> Firestarter (it might prompt you for pass) 
- click on policy tab
- right click on the bottom window "Allow Service" 
- select add rule  and  on the Name field enter BitTorrent or on the Port field enter 6881-6889

---

### Post by nalmeth on 2006-04-11
As far as I know (or have been told), ports 6881-6889 are not recommended, but are set as defaults in most bittorrent apps.
[http://azureus.aelitis.com/wiki/index.php/NAT_problem](http://azureus.aelitis.com/wiki/index.php/NAT_problem)
**> Remember, [don't use ports in the 6881-6999 range]("http://azureus.aelitis.com/wiki/index.php/Port_is_blacklisted") - change it now if you still do, despite Azureus' default port being 6881.**

---

### Post by hbush on 2006-04-11
[QUOTE=nalmeth]As far as I know (or have been told), ports 6881-6889 are not recommended, but are set as defaults in most bittorrent apps.
[http://azureus.aelitis.com/wiki/index.php/NAT_problem](http://azureus.aelitis.com/wiki/index.php/NAT_problem)
****[/QUOTE]

Thank you nalmeth, 

please disregard my post above, or MODs pls delete it... 

thank you again

---

### Post by nalmeth on 2006-04-11
>  how: 
- Programs --> System Tools --> Firestarter (it might prompt you for pass) 
- click on policy tab
- right click on the bottom window "Allow Service" 
- select add rule  and  on the Name field enter BitTorrent or on the Port field enter 6881-6889
This is still important, if he is using a firewall and that is what is stopping bittorrent.
Just replace the 6881-6889 on whatever range you choose to allow.
Should be around the 54000 --> 64000 range I believe? But don't leave *all* those ports open if you really want your firewall to work. Personally I don't need one, but if you're using it, you should use it to the fullest.

---

