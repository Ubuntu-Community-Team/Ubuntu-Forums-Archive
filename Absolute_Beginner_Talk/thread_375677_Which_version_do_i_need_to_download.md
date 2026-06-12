---
title: "Which version do i need to download?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Tag_yer_dead on 2007-03-04
hey guys,
need a little bit of help here, im not a total noob or ne thing im just not sure which version i need to download.  Im trying to download the mono project and heres the link
[http://www.mono-project.com/Downloads]("http://www.mono-project.com/Downloads")

Also, when you click the link, a new window with more links comes up.  If you could help me with that as well, itd be much appreciated (i sound like an idiot)

Thanks Guys

---

### Post by pay on 2007-03-04
```
wget ftp://www.go-mono.com/archive/1.2.3.1/linux-installer/1/mono-1.2.3.1_1-installer.bin
chmod 775 mono-1.2.3.1_1-installer.bin
sudo ./mono-1.2.3.1_1-installer.bin
```

---

### Post by mcduck on 2007-03-04
mono is in Ubuntu repositories, there's no need to download it from any web page. Just install it with apt-get or Synaptic. :D

If you can't find it you need to enable extra repositories first: go to System/Administration/Software Sources and on the 'Ubuntu 6.10'-tab enable universe, multiverse and restriced.

---

