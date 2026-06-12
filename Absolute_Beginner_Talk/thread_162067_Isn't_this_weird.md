---
title: "Isn't this weird?"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-04-18
It happened that I just fount this:

[http://packages.ubuntu.com/breezy/libs/gnustep-back](http://packages.ubuntu.com/breezy/libs/gnustep-back)

This is where one can download the gnustep-back package. I have no ideea what does it do, but look at the first package it depends on. That's right, it depends on ITSELF. I'm sure that:

dpkg -i gnustep-back_bla-bla.deb

would arise dependency problems. Then how on Earth is this supposed to be installed (without apt-get, I wanna know how can it be dpkg-ed)?

---

### Post by htinn on 2006-04-18
I think you're misreading that depend there. What it says is:

gnustep-back (>= 0.9.5)

This just means it will not install unless apt first removes the older version.

---

