---
title: "rar"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by none211 on 2007-01-27
I'm trying to extract some things in rar format. I've been looking around the forum and found people saying to use unrar, but when I try to apt-get it it tells me E: Package unrar has no installation candidate, so I try sudo apt-get update and then try it with no luck. any suggestions, or an idea for a better program?

---

### Post by aliyanage on 2007-01-27
just a quick question, did you already try installing unrar:

```
sudo apt-get install unrar
```

and then right click the file and extract the file?

regards
aliyanage

---

### Post by Pobega on 2007-01-27
> **aliyanage said:**
> just a quick question, did you already try installing unrar:

```
sudo apt-get install unrar
```

and then right click the file and extract the file?

regards
aliyanage

Just so you know, unrar is a nonfree program (They don't charge you, it's just not under GPL). unrar-free is just as good, except you have to use the command line to extract. I personally use unrar-free and I've had no trouble with it.

---

### Post by none211 on 2007-01-27
yes, this is hte result 
E: Package unrar has no installation candidate

---

### Post by CCBalla10 on 2007-01-27
Try archive manager...that is what i use and it works like a charm.  You can just right click on the file you want to unrar and hit extract here....simple as that

---

### Post by none211 on 2007-01-27
it tells me Archive type not supported.

---

### Post by aliyanage on 2007-01-27
In Synaptic Package Manager click Settings -> Repositories then click Add and then Custom and paste this line:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

then do:

```
sudo apt-get update
sudo apt-get upgrade
```

Then you should be able to see another unrar in the Synaptic Package Manager

let me know how it worked out?

---

### Post by aliyanage on 2007-01-27
otherwise maybe this might help you as well...

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_RAR_Archiver_.28_.rar_.29]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_RAR_Archiver_.28_.rar_.29")

---

### Post by none211 on 2007-01-27
thank you, it worked out fine

---

### Post by Brave Heart on 2007-01-31
Hi Every One
I am a new user in Linux (KUbuntu 6.06)
and i have this problem
i install Synaptic Package Manager
i click Settings -> Repositories , but i didnot find "Add" !!!
can any one explain to me how to solve this problem to unrar the rar files .
thanx

---

### Post by Brave Heart on 2007-01-31
:confused: :confused: :confused:

---

### Post by djlyx on 2007-02-01
> **Brave Heart said:**
> Hi Every One
I am a new user in Linux (KUbuntu 6.06)
and i have this problem
i install Synaptic Package Manager
i click Settings -> Repositories , but i didnot find "Add" !!!
can any one explain to me how to solve this problem to unrar the rar files .
thanx

Mine worked after I followed the instructions here:


[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_RAR_Archiver_.28_.rar](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_RAR_Archiver_.28_.rar) _.29

after you follow these instructions, just use archive manager and it works.

---

