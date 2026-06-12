---
title: "Firefox works using my proxy settings but apt-get doesnt!! Please help"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Georgie.Mathews on 2008-01-31
I entered the correct proxy settings in the network settings, i am on this forum using the same settings in firefox, but i cant get any packages to install via apt-get.Plz help.

---

### Post by overdrank on 2008-01-31
> **Georgie.Mathews said:**
> I entered the correct proxy settings in the network settings, i am on this forum using the same settings in firefox, but i cant get any packages to install via apt-get.Plz help.

HI and welcome, is that the error you receive updating your system? Are you using Gutsy Ubuntu? You may want to check your repos. 
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Georgie.Mathews on 2008-01-31
Yes, but nothing seems to be working...also all the [http://help.ubuntu.com](http://help.ubuntu.com)..... sites are down could this be why i cant download and install anything? When i use wget in terminal it works so im sure the proxy settings are working fine.

---

### Post by overdrank on 2008-01-31
> **Georgie.Mathews said:**
> Yes, but nothing seems to be working...also all the [http://help.ubuntu.com](http://help.ubuntu.com)..... sites are down could this be why i cant download and install anything? When i use wget in terminal it works so im sure the proxy settings are working fine.

HI you an try and change the server you are downloading from in software sources located under system, administration.

---

### Post by Georgie.Mathews on 2008-01-31
Hello. Firefox works perfectly fine using the proxy settings (usrname and password). I entered the same network proxy settings in Preferences->Network Proxy. But neither apt-get works (i get 
```

gmathews@The1337UbuntuBox:~$ sudo apt-get install irssi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package irssi[
```

Also when Software sources is run, it tries to reload but I get a 407 error saying incorrect authentication. I am stumped by this as i am using the exact same username and password for firefox which is working perfectly. Please help. Thanks

---

### Post by overdrank on 2008-01-31
> **Georgie.Mathews said:**
> Hello. Firefox works perfectly fine using the proxy settings (usrname and password). I entered the same network proxy settings in Preferences->Network Proxy. But neither apt-get works (i get 
```

gmathews@The1337UbuntuBox:~$ sudo apt-get install irssi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package irssi[
```

Also when Software sources is run, it tries to reload but I get a 407 error saying incorrect authentication. I am stumped by this as i am using the exact same username and password for firefox which is working perfectly. Please help. Thanks

HI and please do not make multiple threads on the same subject
[http://ubuntuforums.org/showthread.php?t=684097](http://ubuntuforums.org/showthread.php?t=684097)
Did you try and change the server location as I suggested in your other thread?

---

### Post by bodhi.zazen on 2008-01-31
You have to configure apt-get to use your proxy.

See this thread : [http://ubuntuforums.org/showthread.php?t=83401](http://ubuntuforums.org/showthread.php?t=83401)

---

### Post by Georgie.Mathews on 2008-02-02
It works. Needed to change the sources.list file by uncommenting all the sources and also following your advice. Thanks!

---

