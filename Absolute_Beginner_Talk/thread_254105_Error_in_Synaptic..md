---
title: "Error in Synaptic."
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by bugz0r on 2006-09-09
E: Type 'http://users.musicbrainz.org/~luks/ubuntu' is not known on line 33 in source list /etc/apt/sources.list
E: Unable to lock the list directory

This is what shows up when i try to open/update/anything with synaptic.
I did something wrong, how do I fix this?

---

### Post by taurus on 2006-09-09
You need to edit your /etc/apt/sources.list and block that site for now maybe because it's down or dead...  You can do that by placing a # in front of that line, [http://users.musicbrainz.org/~luks/ubuntu](http://users.musicbrainz.org/~luks/ubuntu).

```
gksudo gedit /etc/apt/sources.list <-- to edit your /etc/sources.list
sudo aptitude update <-- to update the list
sudo aptitude upgrade <-- to upgrade your system
```

---

### Post by bugz0r on 2006-09-09
thanks so much.

---

