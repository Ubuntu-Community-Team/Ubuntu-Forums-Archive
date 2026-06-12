---
title: "Two broken files"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Want A Pie on 2007-12-13
Hi, I'm trying to get youtube working on my Ubuntu 7.10 Laptop, but I cannot get it working.
When I open a video, it says:
> Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.
I click the popup tab at the top of FireFox which says install missing plugins or something like that.
I click and install the thing there, but many of the files fail to download. If I choose the different option, it fails them, then says I have 2 broken files or something like that.

I hope someone can help me 

Thanks in advance

---

### Post by flamelab on 2007-12-13
Go to Synaptic and choose up in the tool panel Edit -->Fix broken packages .

&#913;s for Firefox , go to [http://www.adobe.com/go/getflashplayer]("http://www.adobe.com/go/getflashplayer"), download the tar.gz file, uncompress it and run in console the **install **.sh file . &#921;t will tell you what to do and you have finished :)

---

### Post by taurus on 2007-12-13
Or you can also try to install them from a terminal with

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin flashplugin-nonfree
```

---

### Post by flamelab on 2007-12-13
> **taurus said:**
> Or you can also try to install them from a terminal with

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin flashplugin-nonfree
```

Or faster :) 

```
sudo aptitude update && sudo aptitude install ubuntu-restricted extras flash plugin-nonfree
```

---

### Post by taurus on 2007-12-13
> **flamelab said:**
> Or faster :) 

```
sudo aptitude update && sudo aptitude install ubuntu-restricted extras flash plugin-nonfree
```

That will not work because you've missed a - and an extra space.

---

### Post by Want A Pie on 2007-12-13
I rebooted and a thing told me I had 145 updates to download.
I downloaded them all, and now I can watch youtube vids, but I can't hear any sound...
anyone know why?

---

### Post by flamelab on 2007-12-14
> **taurus said:**
> That will not work because you've missed a - and an extra space.

:-? Sorry , I was typing really fast ...:(

> I rebooted and a thing told me I had 145 updates to download.
I downloaded them all, and now I can watch youtube vids, but I can't hear any sound...
anyone know why?

Type ```
alsamixer
```and move the bars switchies ( or whatever those are ) so that you can hear sound .

---

