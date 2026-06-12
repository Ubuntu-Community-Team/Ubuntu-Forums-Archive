---
title: "Need help with burning CD from ISO please"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2006-11-17
I have Dapper 6.0 and have downloaded an ISO file, which I can see in my file system >tmp 

When I go to Places >CD creator I don't se how to actually burn the file to the CD and would appreciate some help here.

Thanks.

---

### Post by taurus on 2006-11-17
Use k3b to do your burning.  It's fast and easy and it's available in repos...

```
sudo aptitude update
sudo aptitude install k3b
```

---

### Post by Abild on 2006-11-17
Alternatively, you can simply right click on your ISO and select something like "Burn to disk" (I'm not exactly sure what it's called in the English version of Ubuntu)

If you want a more advanced burning program and don't want to use QT based programs like k3b you could also try gnomebaker (sudo aptitude install gnomebaker). It's not quite as advanced as k3b but it'll get the job done.

---

### Post by L Campbell on 2006-11-17
> **taurus said:**
> Use k3b to do your burning.  It's fast and easy and it's available in repos...

```
sudo aptitude update
sudo aptitude install k3b
```

Thanks for the help.

I got k3b successfully installed but when I try to to make the CD it fails because 'the data won't fit on the disk' (or words to that effect)

Anyway, the file shows to be 678.6MB and the CD is supposed to be 700MB.

A friend has made Ubuntu CD's on these same disks about a year ago.

Is there something I should have done with the downloaded file?

---

### Post by willca on 2006-11-17
There's a lot of nice cd burn software around. But so far gnomebaker is the easiest I've used. 

apt-get install gnomebaker

after the install, just open up a terminal and type gnomebaker

HTH

-W
[www.boondoons.com](www.boondoons.com)

---

### Post by L Campbell on 2006-11-19
> **L Campbell said:**
> Thanks for the help.

I got k3b successfully installed but when I try to to make the CD it fails because 'the data won't fit on the disk' (or words to that effect)

Anyway, the file shows to be 678.6MB and the CD is supposed to be 700MB.

A friend has made Ubuntu CD's on these same disks about a year ago.

Is there something I should have done with the downloaded file?

Finally, I got my CD to burn, using k3b and got the program install on my 'puter.

Its Linux Mint 2.0 (a new distro, see [http://lt.k1011.nutime.de/)](http://lt.k1011.nutime.de/)).  Seems like its Ubuntu with a variation but works very well.

Thanks for all the help.

---

