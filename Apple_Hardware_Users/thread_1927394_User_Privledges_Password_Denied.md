---
title: "User Privledges Password Denied"
date: 2012-02-17
forum: Apple Hardware Users
---

### Post by Javelin Dan on 2012-02-17
I just got done installing a Xubuntu desktop on top of a base (mini) install of Ubuntu 10.10 Ppc on an old Mac G4 Quicksilver. Everything seemed fine till I started to take it around the block and hit my first bump. When I went into synaptic, it of course asked me for my password which I entered and it was denied. I tried many times with no results. This is the same password I used all the way through the install process and in fact, the very same one I logged into that session with. What do I do next?

---

### Post by coffeecat on 2012-02-18
Hi - this sounds as though you don't have sudo mode enabled in gconf settings. If so, this means that Synaptic is prompting for the root password, rather than your account password.  Post the output of this:

```
gconftool -R /apps/gksu
```

If you get the line "sudo-mode = false" in the output, then run:

```
gconftool --set /apps/gksu/sudo-mode -t bool true
```

By the way, I have only a little experience of Xubuntu. I'm fairly sure that Xubuntu uses the same gconf settings as Ubuntu/gnome but not 100%. If you get an error after the first command, don't run the second.

---

### Post by Javelin Dan on 2012-02-18
Thanks Coffee Cat - I'll certainly give that a whirl. Being the weekend, it may take a while before I can find the time, but I'll certainly post my results in the next few days. Thanks again for your time.

---

### Post by Javelin Dan on 2012-02-18
Thanks Coffeecat - the medicine worked just as prescribed and it didn't even taste bad! I simply followed your instructions and I had access to synaptic! One word of caution to other newbs following in my footsteps: there is no output after the second command to confirm that it worked, you simply have to try. I am truly in your debt - thanks again!

---

### Post by coffeecat on 2012-02-18
Excellent. I'm glad that worked. Generally speaking, if you get no output from a terminal command, it means that something has completed successfully. Of course, the "something" may not be what you wanted (:)) but no output is usually a good thing, even if unnerving if you're not used to it.

Good luck!

---

