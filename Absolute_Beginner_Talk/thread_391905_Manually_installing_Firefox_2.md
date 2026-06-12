---
title: "Manually installing Firefox 2"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Mel_K on 2007-03-23
Hello,
it has been a long time since having to install anything and I am stuck.

I downloaded onto my desktop firefox-2.0.0.2.tar.gz and cannot figure out what to do next as there isn't an install read-me and the release note on the mozilla site don't give proper installation instructions either.

I don't want to re-download as I have limited bandwidth until the end of the month.

I am currently using Firefox 1.5.0.10 and Ubuntu 6.06 and I have recently backed up my firefox preferences.

What are my options?
Any advice is welcome, thanks!

---

### Post by aysiu on 2007-03-23
This script will take care of it for you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Irony on 2007-03-24
I can confirm that aysiu+nanotube's script works perfectly on my Dapper installation, I now have the latest version of Firefox (2.0.0.3).

Simply download the script to your desktop and follow aysiu's instructions and everything happens automatically and very clearly.

The repositories still show the 1.5 version - I assume though that this is just providing the dependencies?

---

### Post by khedron on 2007-03-24
Probably, but I'd be wary of updating Firefox through Synaptic - you could overwrite your manually installed one.

---

### Post by igknighted on 2007-03-24
If you are installing manually go to [www.getwiftfox.com](www.getwiftfox.com) and download the install script for your processor.  Swiftfox IS firefox, just custom compiled for different processor to increase its speed.  (you get the benefits of custom compiled, but someone else did the work).  It will install swiftfox to /opt if you run the script as root so you don't have to worry about overwriting your current firefox.  Also, it should automatically pull in all your FF settings and plugins, so you don't have to set it up yourself.

---

### Post by aysiu on 2007-03-24
> **khedron said:**
> Probably, but I'd be wary of updating Firefox through Synaptic - you could overwrite your manually installed one.
Actually, they're completely separate. Some people choose not to update through Synaptic, though, just because of the seeming redundancy.

By the way, the aforementioned Firefox script does everything igknighted describes the Swiftfox as doing... but for Firefox instead.

---

### Post by Irony on 2007-03-24
aysiu, should I uninstall the Firefox 1.5 showing in synaptic, is it just taking up diskspace?

---

### Post by aysiu on 2007-03-24
> **Irony said:**
> aysiu, should I uninstall the Firefox 1.5 showing in synaptic, is it just taking up diskspace?
Not according to [the Ubuntu Wiki page on Firefox](https://help.ubuntu.com/community/FirefoxNewVersion): > Warning: If you use this guide, do not remove the Ubuntu version of Firefox. Doing so will break the following packages: Yelp (help viewer), Epiphany, Gnome-app-install (Add Applications), Liferea, Blam and any application requiring the Gecko rendering engine.

---

### Post by Irony on 2007-03-24
Ah good point aysiu - I actually read it but forgot about that bit. Thanks.

---

