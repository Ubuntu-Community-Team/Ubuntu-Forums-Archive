---
title: "Dell latitude Neomagic sound card - freezes on &quot;loading hardware drivers&quot;"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-15
I have a Dell Latitude, older (128 mb of ram, etc.)  Sometimes when booting it freezes at "loading hardware drivers".  I know it has something to do with the sound drivers and my sound card.  It's a common problem among Dell Latitudes. 

I want to know if there is a way to get rid of alsa drivers (the drivers that are messing up my system) and use the oss drivers.  Now I'm very new at linux, I'm not sure if you can use oss drivers for your system, or how it really works, so help would be very much appreciated.

---

### Post by %hMa@?b&lt;C on 2006-06-15
if you press <ctrl>+<c> when it hits the loading driver thign, does it boot up fine?

---

### Post by WADemosthenes on 2006-06-15
[QUOTE=jeffc313]if you press <ctrl>+<c> when it hits the loading driver thign, does it boot up fine?[/QUOTE]

No, nothing happens.

---

### Post by WADemosthenes on 2006-06-15
[QUOTE=WADemosthenes]No, nothing happens.[/QUOTE]

P.S. 
when I say it "sometimes" freezes I mean "most of the time" :P

---

### Post by WADemosthenes on 2006-06-22
I'm really sorry, I'm just really new at this.  I think I found the bug at: [https://bugzilla.ubuntu.com/show_bug.cgi?id=7939](https://bugzilla.ubuntu.com/show_bug.cgi?id=7939)  Took me long enough :D.  Anyway, most of what it talks about it way over my head, if someone could help me...?  Thanks!!

---

