---
title: "macbook Darwin 10.6.0 -&gt; ubuntu"
date: 2011-03-02
forum: Apple Hardware Users
---

### Post by ***** on 2011-03-02
Hi, i want to install ubuntu on my macbook pro:

 Version du système :	Mac OS X 10.6.6 (10J567)
 Version du noyau :	Darwin 10.6.0

i can't find which version i need : 10.04, 10.10 , 32/64 ?

i want to run both system OSX and ubuntu : tipps, links for the installation ?

thank you

---

### Post by Colin Rovis on 2011-03-02
1) bootcamp -- lets say 40 GB
2) boot with ubuntu 10.10 32bit (or 64 bit, if your Macbook is 64bit)
3) install ubuntu on the partition created via bootcamp

*IMPORTANT* Don't let ubuntu install the grub into MBR, but into the partition created with bootcamp!

4) install rEFIt

enjoy!

You should backup your data first with Carbon Copy Cloner to an external harddisk, so in case you destroy your OS X you can easily return ...

ss
Colin

---

### Post by watgrad on 2011-03-02
First find our what macbook pro version you have.  Then follow the directions on the macbook pro specific webpage for your hardware:

[https://help.ubuntu.com/community/MacBookPro5-5](https://help.ubuntu.com/community/MacBookPro5-5)


For eg.  if you have a macbook pro 6-2 and you want to install 10.04 (lucid) on it select the MacBookPro6-2/Lucid site.

I've used these directions to install Lucid on a macbookpro5-2 and  Maverick on a macbookpro7-1 with only a few minor hitches.  The people in these forums will be able to help you solve any snags you encounter.

---

