---
title: "deluge won't connect"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by CrashintoDMB on 2007-08-04
i can't seem to figure out how to make deluge torrent client to work. i have it downloaded and installed and can run, but when i load a torrent in it, it does not connect to any peers or seeders. any help?

---

### Post by benx009 on 2007-08-04
are you sure that it's not just the torrent that has problems (no seeders/peers)?  if you are sure it's not the torrent, then perhaps the bittorrent port deluge is using is closed?  you can use [firestarter]("http://www.fs-security.com/") to configure your ports

---

### Post by apswartz on 2007-08-04
Oh my, where to begin?

1. Did you try more than one torrent file?

2. Does another torrent program work? e.g., ktorrent

3. Are you behind a firewall?

Let's start with these.

---

### Post by CrashintoDMB on 2007-08-04
First of all, i cant seem to get firestarter installed. secondly, i changed the ports with my router, and although the UDP port opens, the TCP does not. I've changed it twice now to no avail. To answer Apswartz's questions, 1. yes 2. haven't tried/cant figure it out (hey, im new) 3. I dont think so. does ubuntu come with one?

---

### Post by Aurdal on 2007-08-04
Ubuntu comes with the basic bittorrent client, however you probably don't want to use that as it opens up a new window for each torrent.

You could install some other program though. On the applications menu click on "Add/Remove..." and search for torrent. You should be able to install ktorrent fairly easily.

If you want you could also try Azureus, open up a terminal (Applications > Accessories > Terminal) and type in "sudo apt-get install azureus", hit enter, type in your password and hit enter again. :)

---

### Post by apswartz on 2007-08-04
Let me recommend ktorrent...
```
sudo aptitude install ktorrent
```

If you don't already have the needed kde libraries installed it will ask to install those as well.

---

### Post by CrashintoDMB on 2007-08-04
okay we'll ill give ktorrent a try and see what happens. if something doesnt work ill post again. thanks

---

### Post by CrashintoDMB on 2007-08-04
okay so. haha. it says that the port i opened is blacklisted. that sounds really bad.

---

### Post by apswartz on 2007-08-04
Sounds like some kind of firewall. Describe your network and how you are connected to the internet and your internet provider.

---

### Post by CrashintoDMB on 2007-08-04
i've got a d-link router which runs a line directly to my computer. i have comcast. um. haha. i dont think i have a firewall on here unless ubuntu comes with one. i couldnt figure out how to get firestarter running so i dont know if that could help me at all...

---

### Post by apswartz on 2007-08-04
Okay, I just googled it and it is the torrent provider that is blocking that port.

Go to "Settings" > "Configure ktorrent"

and change your port number

---

### Post by Aurdal on 2007-08-04
Read this:
[http://www.azureuswiki.com/index.php/PortIsBlacklisted](http://www.azureuswiki.com/index.php/PortIsBlacklisted)

---

### Post by CrashintoDMB on 2007-08-04
wonderful. got it. thanks a lot guys.

---

### Post by Ptero-4 on 2007-08-04
CrashintoDMB. Ubuntu does come with a firewall built-in, you need to run firestarter from the System>Administration menu and it will ask for your password.

---

### Post by apswartz on 2007-08-04
Thanks for the link Aurdal. I wondered why the port would be blacklisted. Makes perfect sense now.

---

### Post by Aurdal on 2007-08-04
Glad I could help. :)

---

