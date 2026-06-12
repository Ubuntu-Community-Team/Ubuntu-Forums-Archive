---
title: "BitTorrents- No upload"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Ian505 on 2008-01-14
Whenever I download a torrent, I cant get anything uploaded- so my downloads are painfully slow. (less than dial up on ADSL) I fowarded a port to BitTornado (my client) for the uploads on my router... but still no luck. Any ideas?

-Ian

---

### Post by nikoPSK on 2008-01-14
> **Ian505 said:**
> Whenever I download a torrent, I cant get anything uploaded- so my downloads are painfully slow. (less than dial up on ADSL) I fowarded a port to BitTornado (my client) for the uploads on my router... but still no luck. Any ideas?
 
-Ian
 
try another client please. :)
 
nikoPSK

---

### Post by Het Irv on 2008-01-14
Sad but true,  Some ISP block Torrents.  I know that Comcast users have about a 66% chance that it will be blocked and that may be what is happening to you.  As long as all of the firewalls (hardware and Software) between you and the Internet are allowing that program to send packets it should work.

What Firewalls do you have running between you and the Internet?

---

### Post by KevinD_Atl on 2008-01-14
[FONT="Tahoma"]I had the same problem only my speeds were PAINFULLY slow.  I use K-Torrent and my ISP is Comcast.  The only thing that helped was turning off DAS (i think that's the wrong letters, but's the tracking thing)  After I turned it off, my speeds are flying all day and night.[/FONT]

---

### Post by thelatinist on 2008-01-14
Try checking the port you've opened using [http://www.canyouseeme.org/](http://www.canyouseeme.org/).  If the port is in fact open, then try another torrent client (I suggest Deluge).

---

### Post by Ian505 on 2008-01-14
I checked out Deluge as a client, and I love just about anything written in Python- and this is no exception. However, as I downloaded Deluge, I checked my Torrent I had running in the background in BitTornado.

Take a look.
[[IMG]http://img178.imageshack.us/img178/2661/bittornadozr2.th.png[/IMG]](http://img178.imageshack.us/my.php?image=bittornadozr2.png)

So apparently I can upload... and it looks like the torrent I was trying to download wasn't seeded.... duh. I feel so stupid. As for only a 2/3 chance of success... I hope that isn't for Verizon DSL. (Yes, I wanted Comcast... but there is NO WAY I am paying $2500 to have a cable laid and then pay the same premium as the guy down the street.)

Whats weird is that canyouseeme said that the port I had fowarded was blocked... (And how would the site 'no-ip' solve this kind of problem? (see canyouseeme.org)

DAS? Are you talking about NAS, or network access storage? Like a online hard drive?

---

### Post by Terry of Astoria on 2008-01-14
Using Azureus you can set the port to use. Azureus also has a cool distributed database that enables torrents whose tracker is down! It's really great.

---

### Post by thelatinist on 2008-01-14
> **Ian505 said:**
> Whats weird is that canyouseeme said that the port I had fowarded was blocked... (And how would the site 'no-ip' solve this kind of problem? (see canyouseeme.org)

Did you have your bittorrent client open at the time? You will get a "connection refused" error if not, even if the port isn't blocked. 

> DAS? Are you talking about NAS, or network access storage? Like a online hard drive?

Maybe s/he meant DHT?

---

### Post by Ian505 on 2008-01-14
Yea, that was the problem with the port. (Whats DHT?) 

Also, I am looking for a nice, easy to use program that handles all kinds of downloads- not just torrents. Any reccommendations?

---

### Post by nikoPSK on 2008-01-14
miro, or opera. :KS

---

