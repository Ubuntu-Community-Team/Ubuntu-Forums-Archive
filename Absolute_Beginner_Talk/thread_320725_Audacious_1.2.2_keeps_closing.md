---
title: "Audacious 1.2.2 keeps closing"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by suki on 2006-12-17
I've added these to the repository:
deb [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) edgy main
deb-src [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) edgy main

And audacious after a few songs played it will close on it's own. Does anyone know how to fix this?

---

### Post by xyz on 2006-12-17
Hi,
You might want to take a look at:
[Audacious FAQ]("http://audacious-media-player.org/FAQ")
This is strange! Let me know what you find out. Thx.

---

### Post by OffHand on 2006-12-18
Start it from the command line and see what info you get when it crashes.

---

### Post by nenolod on 2007-02-23
Well, there is any number of issues which could make 1.2 crash. Essentially, 1.2 has a lot of bad design practices inherited from BMP and XMMS. While we had cleaned up a lot of the code, we found out that we needed to redesign a lot more to get things to run reliably.

My suggestion would be to try 1.3.0 when it gets out.

---

