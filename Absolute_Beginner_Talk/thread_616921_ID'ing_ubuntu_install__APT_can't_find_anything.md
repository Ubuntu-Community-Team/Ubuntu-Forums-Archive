---
title: "ID'ing ubuntu install / APT can't find anything?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by firestorm_v1 on 2007-11-18
Got two new questions for y'all

1:  I'm having problems identifying which installation of Ubuntu that I have.  In RedHat there was /etc/redhat-release which would return something like "Red Hat Linux release 7.3 (Valhalla)"  In Ubuntu, I can't find any such marking, and when I burned the iso image (just before I deleted it) all I did was mark the CD "ubuntu-server install".  I'm hearing names like "Dapper"and "Edgy" and I'm guessing that's like the name "Valhalla" from above? Correct?

2: Apt seems to work well with most packages but I can't locate jabber-server, jabberd, sun-java6-bin or ejabberd.  There are a lot of HOWTO's for installing a jabber server that says that all I need to do is apt-get install (package) but the packages aren't there?  What is the process for updating Apt so I can find the packages I need?


Thanks again for all your help!

---

### Post by MegaJim on 2007-11-18
Hey there :)

the simplest way to find out what you've got through a terminal is

```
uname -a
```

as for jabber, you need to find a repository for your distro (whichever that is!) which provides it, or install through a .deb package or source.

---

### Post by MegaJim on 2007-11-18
Oh I just realised that what you might actually need is to find out the codename of your distribution am I right?

```
lsb_release -c
```

or 

```
lsb_release -a
```

for the whole shabbang!

---

### Post by firestorm_v1 on 2007-11-22
That helped tons!

The thing now is that I found a site that had an automatic script that would create an apt-sources file for me and now danged if I can't find it.  I have tried googling it and searching the forums, but turned up nothing.

I remember that the site was ubuntu branded and it asked me for distro specific information, then when I hit submit, it gave me a apt-sources list and I was then able to apt-get install the packages I was initially looking for.

Do you or anyone by chance know the site that I can't remember?

---

### Post by firestorm_v1 on 2007-11-22
Found it!!

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

It will generate a file for /etc/apt/sources.list based on the information you give it.  Have fun!

---

