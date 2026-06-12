---
title: "Where are the software updates to Ubuntu stored on my PC?"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by emarkay on 2007-02-11
Are ALL the security updates and other updates  found in a new installation of Ubuntu, stored as .deb files  in /var/cache/apt?

Is is safe to presume that by using AptonCD, EVERY downloaded update (all 140 megs of them, as of now), as well as my downloaded (manually selected) updates to programs and new programs are there?

So this is the only CD  the onecreated by AptonCD) I will need for a "up-to-the-minute" OFFLINE Ubuntu installation?  

Thanks.

---

### Post by aysiu on 2007-02-11
As long as you haven't deleted the cache through Synaptic or run one of these two commands from the terminal, then all of them should be in /var/cache/apt/archives ```
sudo apt-get clean
``` ```
sudo aptitude clean
```

---

### Post by emarkay on 2007-02-11
So even if it's (for example) a FireFox or OO update, it's there?

---

### Post by aysiu on 2007-02-11
Yes.

---

