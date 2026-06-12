---
title: "Need newbie help with installing!"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by jokerjake on 2007-11-06
Right, i've been having troubles installing loads of programs / packages on linux, and have been researching how i do it properly for ages now! but nothing seems to work.

_E.g._ 

I downloaded teamspeak (Linux) from there site, extracted it >>> went into terminal >>> linked to the file and added teamspeak2rc2-install at the end (which worked for downloading something else, so i did it with this too)

but all i got was :::

jake@linux:~$ /home/jake/Downloads/ts2_client_rc2_2032/setup.data/installer/inst
aller teamspeak2rc2-install **undefined symbol: initPAnsiStrings**

I also checked the install file was executable enabled, it was, tryed normal clicking it ... nothing...

Am i doing something wrong? if so i'd love some guidence :]  
cheers - jake

---

### Post by netbandit on 2007-11-06
You might want to try doing things the Ubuntu way:

```
apt-get install teamspeak-client
```

Have Fun!
-nb

---

### Post by jokerjake on 2007-11-06
```
jake@linux:~$ apt-get install teamspeak-client
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

---

### Post by akiratheoni on 2007-11-06
> **jokerjake said:**
> ```
jake@linux:~$ apt-get install teamspeak-client
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

If you have Synaptic Package Manager open, close it, then try:

```
sudo apt-get install teamspeak-client
```

---

### Post by rudeboyskunk on 2007-11-06
Also, make sure all of your repositories are enabled by going to System>Administration>Software Sources and enabling multiverse, universe, restricted, etc.  You have to close Synaptic before doing this.

---

### Post by netbandit on 2007-11-06
> Also, make sure all of your repositories are enabled by going to System>Administration>Software Sources and enabling multiverse, universe, restricted, etc. You have to close Synaptic before doing this.

I think teamspeak is in the standard repositories.  It shows up on my system and I haven't added anything to it.

-nb

---

