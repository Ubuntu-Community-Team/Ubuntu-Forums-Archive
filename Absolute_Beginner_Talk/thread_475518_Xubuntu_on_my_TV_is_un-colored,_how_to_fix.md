---
title: "Xubuntu on my TV is un-colored, how to fix?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by hobs0n on 2007-06-16
I finally managed to install Xubuntu on my new server. Im gonna read up and learn how to handle it as ICS, FTP server, MediaCenter server, DC clients, Torrent clients and so on but my first step is to get it to be accept Remote Desktop connections from my main computer with windows XP on it. Anyone got a good url to a guide for that or do I have to use VNC? IIRC the last time I used VNC it basically sucked compared to windows Remote Desktop, took way more bandwith and just very slower but that might have changed? My second first starter problem here is that since Im gonna use my new server as a Media Center I dont have a regular screen connected to it, only my TV. Its an old regular PAL TV. The problem is that the screen is un-colored, as is the video card is sending out NTC signals. How do I fix this?

The server hardware is:

[	MSI K9AGM2-FIH, AMD 690G+SB600](http://global.msi.com.tw/index.php?func=proddesc&prod_no=1165&maincat_no=1&cat2_no=171) as motherboard and [Asus 6200LE](http://www.asus.com.tw/products.aspx?l1=2&l2=6&l3=497&l4=0&model=1165&modelmenu=1) graphic card.

---

### Post by Golyadkin on 2007-06-16
VNC works fine nowadays, and if you are gonna use it on your local network anyway (100 Mbit/s LAN, or even 54 Mbit/s WLAN) the bandwidth is not an issue. Check out: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

About the NTSC/PAL thing, I don't know. Can't you select what output your video signal has?

---

### Post by hobs0n on 2007-06-16
> **Golyadkin said:**
> VNC works fine nowadays, and if you are gonna use it on your local network anyway (100 Mbit/s LAN, or even 54 Mbit/s WLAN) the bandwidth is not an issue. Check out: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

About the NTSC/PAL thing, I don't know. Can't you select what output your video signal has?

Ok Im trying VNC then :)

Hm where can I see that? Just installed so I know pretty much nothing, only place to change settings was in the screen options where I could only change resolution and color settings.

---

### Post by Titus A Duxass on 2007-06-16
You have to modify your xorg.conf file.
Do a search on the forum for TV-out and do a bit of reading.

---

### Post by hobs0n on 2007-06-16
ok, thanx!

---

