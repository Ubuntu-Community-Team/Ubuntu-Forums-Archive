---
title: "How to remove programs from update manager?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by lefen on 2007-08-03
Hay all. If i dont want to install a particular software update, how do i permanently remove it from the update manager?

Thanks :>

---

### Post by Rocket2DMn on 2007-08-03
Have a look here, I used this to keep my wine version at 0.9.39
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin)

---

### Post by dpar on 2007-08-03
Doesn't Package>Lock Version work too?

---

### Post by Rocket2DMn on 2007-08-03
> **dpar said:**
> Doesn't Package>Lock Version work too?

Ah, it looks like Synaptic has a Lock Version and Force Version option under Package.  I prefer to use the CLI with apt-get, but I suppose that would work, too.  Looks like Lock will keep youre current one and Force will go get a different version if you don't currently have it.
Use whichever you're more comfortable with.

---

### Post by lefen on 2007-08-03
Thanks guys. You win.

---

