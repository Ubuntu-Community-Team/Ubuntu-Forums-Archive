---
title: "Synaptic Package Manager Question"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by JengaBlocks on 2007-03-26
I want to get the ndisgtk package and noticed that when I do a search with Synaptic, it doesn't show up. However, when I go to the [Ubuntu Package Site]("http://packages.ubuntu.com/edgy/net/") it is in there.

Is there a way to point the Synaptic PM to the Ubuntu packages domain? Is there a reason why SPM isn't pointing there by default?

---

### Post by cowlip on 2007-03-26
That package is in the universe repository, have you enabled it?  You'll have to refresh apt after that.

---

### Post by Penguin Power on 2007-03-26
JengaBlocks, you need to enable the universe/multiverse repositories

Go to system>adminstration>software sources and enable it, or it can be done in the preferences of Synaptic.

Close all instances of Synaptic (updates, synaptic, apt-get in terminal etc) before you update the software sources to avoid bugs n' errors.

The Ubuntu Edy Wiki has some good info if you need to add extra repositories.

---

