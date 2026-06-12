---
title: "[SOLVED] g4 powerbook hangs after hardy install"
date: 2008-07-25
forum: Apple Hardware Users
---

### Post by johnrobert on 2008-07-25
I just did a clean install of Hardy on my 15" G4 powerbook. Everything seemed fine during the install, but now, after the boot prompt, the screen goes dark and that's the end of it.

I can reach a shell in my new installation by booting to "rescue" on the alternate install CD. But I don't know what I should be editing, or how to go about that. The only thing I've tried is editing my yaboot.conf to include

```
append="nosplash video=radeonfb:1024x768-24@60"

```
as was suggested elsewhere in this forum. But that didn't help.

Suggestions or pointers?

---

### Post by stream303 on 2008-07-25
Once you make those changes in /etc/yaboot.conf, you need to make the system aware of it with:

```
sudo ybin -v -C /etc/yaboot.conf
```

---

### Post by johnrobert on 2008-07-25
Stream,

Dude, thank you. It's purring (actually it's displaying) like a kitten now. Next up: testing out that rumor I heard that the Gnash package actually works under Hardy.

Thanks again!

---

