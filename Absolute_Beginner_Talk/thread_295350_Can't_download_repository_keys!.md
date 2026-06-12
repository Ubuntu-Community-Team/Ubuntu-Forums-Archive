---
title: "Can't download repository keys!"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by shingalated on 2006-11-07
I'm trying to enable the repositories to download and install software and when I reload the package list with 'apt-get update' or in synaptic, I am unable to download any of the gpg keys that are required. The router that I am on uses port 8080 for remote management and can not be disabled. This is what I get when I do 'sudo apt-get update':

```
Err http://www.getautomatix.com dapper Release.gpg Could not connect to 192.168:8080 (192.0.0.168), connection timed out
```

I get this for each key that needs to be downloaded. Is there a way to get and install the keys without using port 8080?

---

### Post by taurus on 2006-11-07
Open a terminal and type

```

wget http://www.getautomatix.com/apt/key.gpg.asc
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -

```

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29)

---

### Post by shingalated on 2006-11-07
I'm at home right now but i will give that a try at school tomorrow.  I am setting up a server for my teacher.

---

### Post by shingalated on 2006-11-08
This happens not just with the automatix key, but also with the basic Ubuntu repository keys (the Release.gpg keys)

---

