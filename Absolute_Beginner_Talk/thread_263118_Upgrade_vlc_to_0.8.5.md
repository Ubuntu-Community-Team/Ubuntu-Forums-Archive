---
title: "Upgrade vlc to 0.8.5"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by ron999 on 2006-09-22
I'm trying to upgrade vlc to version 0.8.5
I've added the line to my sources.list:-
deb [http://nightlies.videolan.org/build/dapper-i386](http://nightlies.videolan.org/build/dapper-i386) / 
But now Synaptic is asking for a public key:-
NO_PUBKEY C367D8B981CACA84
What do I do now?

---

### Post by Anduu on 2006-09-22
Enter these lines into a terminal one at a time

```
gpg --keyserver subkeys.pgp.net --recv [COLOR="Red"]KEY[/COLOR]
gpg --export --armor [COLOR="Red"]KEY[/COLOR] | sudo apt-key add -
```

[COLOR="Red"]KEY[/COLOR] being C367D8B981CACA84 in this case.

---

### Post by ron999 on 2006-09-23
Thanks for your reply Anduu.
That did the trick.:D

---

### Post by Anduu on 2006-09-23
No sweat ;)

---

