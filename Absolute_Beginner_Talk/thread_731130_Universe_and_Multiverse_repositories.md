---
title: "Universe and Multiverse repositories"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by ni ni on 2008-03-21
hello All,


I want to enable the universe and multiverse repositories.  do i need to have ubuntu installed or can i do this while booting from the cd?


as root:
when i type   sudo /etc/apt/sources.list    i get command not found.
when i type    /etc/apt/sources.list    i get permission Denied.


Please help?

---

### Post by spiderbatdad on 2008-03-21
Universe and Multiverse are  software sources of packages not contained on the live cd; nor can the live cd accommodate the packages contained in those sources. 
If running off the live cd, it is your only software source. You cannot write to it; and there is no file system on your hard disk to write to.

You would need to install Ubuntu to make use of the additional software sources. If you have a working internet connection during the installation, the extra repositories will be included by default.

---

### Post by bodhi.zazen on 2008-03-21
your command is a little off:

```
sudo nano /etc/apt/sources.lst
```

or

```
gksu gedit /etc/apt/sources.lst
```

You can enable the reops on both the live CD and a HD installation.

---

### Post by TeoBigusGeekus on 2008-03-21
When you install Ubuntu, go to System->Administration->Synaptic
Then go to Settings->Repositories
Ubuntu software tab and tick whatever you want.

---

### Post by alzie on 2008-03-21
You can try clicking system, administration, software sources, (I'm not sure if you'll be asked a password here) then click on universe and multiverse

apparently I'm way slow today  lol :)

---

