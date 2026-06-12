---
title: "Amarok eating resources"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2008-02-08
I installed Amarok a few days ago, and at first it worked fine. I added a few new songs to my library and now when it opens it uses 100% of the CPU until I tell it to stop trying to update the library (when I say I added a few new songs I mean 5-10, not 50+); however, now when it starts a new song on my current playlist it also spikes to 100%. This is quite annoying when I'm trying to write programs (re: perl homework) in the background and it freezes :(

Thoughts?

---

### Post by Jewfro_Macabbi on 2008-02-08
Try switching from the default SQLite db management system to postgresql. postgresql is a faster database system - therefore amarok processes your collection faster using it. You have to install postgresql and set it up first. Then tell amarok to use it.

Instructions here:

[http://scarah-rosenschvitz.blogspot.com/2008/02/setting-up-postgresql-for-amarok-in.html](http://scarah-rosenschvitz.blogspot.com/2008/02/setting-up-postgresql-for-amarok-in.html)

---

### Post by santiagoward2000 on 2008-02-08
> **nonpareilpearl said:**
> I installed Amarok a few days ago, and at first it worked fine. I added a few new songs to my library and now when it opens it uses 100% of the CPU until I tell it to stop trying to update the library (when I say I added a few new songs I mean 5-10, not 50+); however, now when it starts a new song on my current playlist it also spikes to 100%. This is quite annoying when I'm trying to write programs (re: perl homework) in the background and it freezes :(

Thoughts?

Well, Amarok is quite heavy. I had the same problem when I was using it. You could try with something lighter. Exaile is a good GTK alternative, very similar to Amarok, but lighter.
Personally, I love MOC, but that's me...
Cheers!

---

### Post by jaytek13 on 2008-02-08
You can also consider disabling the "scan folders recursively" and "watch for folder changes" options under the amarok settings. It should in the least bit save you a lot of that cpu at start up.

---

### Post by nonpareilpearl on 2008-02-09
Thank you for the responses! I think I'll see if I like Exaile before I do much with reconfiguring Amarok.

Thanks again!

---

### Post by nikoPSK on 2008-02-09
no offense to the k fans, it's a bit of a hog... :cry:

---

### Post by santiagoward2000 on 2008-02-09
> **nonpareilpearl said:**
> Thank you for the responses! I think I'll see if I like Exaile before I do much with reconfiguring Amarok.

Thanks again!

You're welcome! Tell us how it goes!

> **nikoPSK said:**
> no offense to the k fans, it's a bit of a hog... :cry:

:lol: Yes...

---

### Post by nikoPSK on 2008-02-09
> **santiagoward2000 said:**
> You're welcome! Tell us how it goes!



:lol: Yes...

sadly... but I wish rhythmbox came with a bit better support.

---

### Post by santiagoward2000 on 2008-02-09
> **nikoPSK said:**
> sadly... but I wish rhythmbox came with a bit better support.

Hmm... MOC is perfect for me :guitar:

---

### Post by jordanmthomas on 2008-02-09
> **santiagoward2000 said:**
> Hmm... MOC is perfect for me :guitar:

mpd and mpc are all you need.  :guitar:

---

### Post by santiagoward2000 on 2008-02-09
> **jordanmthomas said:**
> mpd and mpc are all you need.  :guitar:

I haven't tried it, but I don't like the way it looks. MOC is more intuitive imho.

---

### Post by jordanmthomas on 2008-02-09
> **santiagoward2000 said:**
> I haven't tried it, but I don't like the way it looks. MOC is more intuitive imho.

It doesn't look like anything.  :confused: 
You don't see any part of it.

Anyway, to each his own.  :)

---

### Post by santiagoward2000 on 2008-02-09
> **jordanmthomas said:**
> It doesn't look like anything.  :confused: 

:lolflag: Well, that's what I think I meant :confused:

> **jordanmthomas said:**
> Anyway, to each his own.  :)

Of course, that's the fun of this!

---

### Post by nikoPSK on 2008-02-09
> **santiagoward2000 said:**
> Hmm... MOC is perfect for me :guitar:

I'll be sure to try that,. :)

---

### Post by santiagoward2000 on 2008-02-09
> **nikoPSK said:**
> I'll be sure to try that,. :)

I hope you enjoy it as much as I do! :KS

---

### Post by nikoPSK on 2008-02-09
> **santiagoward2000 said:**
> I hope you enjoy it as much as I do! :KS

well, I've been to songbird, floola, etc etc etc... so I might like it!

---

