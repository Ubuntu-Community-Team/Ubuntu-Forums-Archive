---
title: "Azureus Annoyance"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-22
When I open up Azureus, I might get an error such as:

Warning - If you have a router/firewall, please check that you have port 27967 UDP open. Decentralised tracking requires this.

However, when I try to click "Hide," it does not go away. How can I dismiss this error?

---

### Post by meng on 2006-10-22
It's a bug with Azureus as implemented in Dapper. You can download the latest Azureus2.jar file and overwrite your existing one, or else you can cross your fingers and hope that it's fixed in Edgy.

---

### Post by shanepardue on 2006-10-22
I believe if you download Azureus from their website, those problems don't 
exist. I may be wrong though. Meng's method definitely works as that's what I
 did.

---

### Post by skymt on 2006-10-22
> **meng said:**
> It's a bug with Azureus as implemented in Dapper. You can download the latest Azureus2.jar file and overwrite your existing one, or else you can cross your fingers and hope that it's fixed in Edgy.

It's fixed in Edgy. ;)

---

### Post by d3v1ant_0n3 on 2006-10-22
Might want to check you have that port forwarded in your router too- it'll speed up your downloads and uploads no end;)

---

### Post by meng on 2006-10-22
> **skymt said:**
> It's fixed in Edgy. ;)
Great news.

---

### Post by redDEADresolve on 2006-10-22
you can download it from its home page or you can check out Automatrix2 and get it from there. It's super easy and helps you install a bunch of other stuff too.

Remember to unistall your old azuerus copy first.

And Google "port forwarding Azuerus" to learn how to forward your ports

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by amitroy5 on 2006-10-22
When will Edgy come out? Will it install the new Firefox 2?

---

### Post by skymt on 2006-10-23
> **amitroy5 said:**
> When will Edgy come out? Will it install the new Firefox 2?

This Thursday, and yes.

---

### Post by Ollan on 2006-10-23
> **redDEADresolve said:**
> you can download it from its home page or you can check out Automatrix2 and get it from there. It's super easy and helps you install a bunch of other stuff too.

Remember to unistall your old azuerus copy first.

And Google "port forwarding Azuerus" to learn how to forward your ports

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

Azureus is not included in Automatix-script?! I can't find it in Automatix2 for Edgy?!

---

### Post by meng on 2006-10-23
Then it's time to install from repositories!
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Ollan on 2006-10-24
The one from rep doesn't work in Edgy?! The splash screen hangs up.

---

### Post by kvonb on 2006-10-24
The Azureus available through Automatix is a bit wierd, it comes up with a very odd main page, I used the latest from Azureus' download page.

Also you might want to update your copy of Java, I believe what you are experiencing is caused by the older (1.4) version of Java.

To check which version of java you are running, type the following into a terminal:

```
java -version
```

If it is less than 1.5 then do the following:

```
sudo apt-get install sun-java5-jre sun-java5-plugin
sudo update-alternatives --config java
```

That should solve it.

---

### Post by delphiguy on 2006-10-24
Its this problems with Azureus that I decided to abandon it.  And stick with uTorrent, uTorrent works great in wine, except for the window flickering, but I can live with that as long as it does its job im very much happy with it.

---

### Post by Ollan on 2006-10-24
> **delphiguy said:**
> Its this problems with Azureus that I decided to abandon it.  And stick with uTorrent, uTorrent works great in wine, except for the window flickering, but I can live with that as long as it does its job im very much happy with it.

Isn't uTorrent a Winows-appliction?

---

### Post by Perfect Storm on 2006-10-24
Howto: azureus the non repo way - [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)
(also tested on breezy, dapper and edgy)

---

### Post by skymt on 2006-10-24
> **Ollan said:**
> Isn't uTorrent a Winows-appliction?

Yes, but as the post you replied to said, it works fine in Wine.

Hey, that should be the new Wine slogan! "It Works Fine in Wine!"

---

