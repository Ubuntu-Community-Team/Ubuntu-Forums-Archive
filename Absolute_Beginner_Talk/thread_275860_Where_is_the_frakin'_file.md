---
title: "Where is the frakin' file?"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Chickenfoot on 2006-10-12
Hello everyone,

I'm new to Linux. I've been searching the forums with little luck.

Here's my n00b question:

I am attempting to download Limewire for Red Hat. I found the torrent, and am using FireFox as my browser. FireFox gives me the choice of which torrent program I wish to use. Freeloader is the default, but I wanna choose KTorrent. 

/home/chickenfoot/Desktop/Frreloader.png

When I hit the drop down arrow, it gives me the choice of "OTHER" When I hit that, I get this:

/home/chickenfoot/Desktop/Where.png

I'm new, so could some one tell me what the Linux equivalent to the Programs folder is? Where are my programs hiding? No idea whre to look, I would greatly appreciate it!

\\:D/

---

### Post by Iarwain ben-adar on 2006-10-12
Hi,
the linux equivalent is normally /etc/bin

So you would go 'searching' for Ktorrent in the /etc/bin folder


Iarwain

---

### Post by towsonu2003 on 2006-10-12
you can use locate or which to locate it as well. either one of these would work (well, depending on the upper-lower case of ktorrent's file name :) )

```

sudo updatedb #not everytime you use locate, just refreshing the database
locate ktorrent

```
or
```

which ktorrent
```

---

### Post by Chickenfoot on 2006-10-12
Holy Ubuntu Beans, Batman!!

Much thanks, towsonu2003 & Iarwain ben-adar!!

That did the trick

:-D

---

### Post by nalmeth on 2006-10-12
Now that it's sorted out, when are you going to install ubuntu? :p

---

