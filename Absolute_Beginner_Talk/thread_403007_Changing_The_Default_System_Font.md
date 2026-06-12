---
title: "Changing The Default System Font"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by VileTimes on 2007-04-06
I've installed Fluxbox over an Ubuntu 6.10 Server installation and I'd really like to change the default system font for various applications. Fonts for Swiftfox were easily changed by modifying the userChrome.css file, but how would I change the font for something like Geany?

I've included a screenshot to illustrate what I'm referring to.

---

### Post by VileTimes on 2007-04-06
Resolved!

For those without a handy control center who want to change their default X11 font, create a file in your home directory called .gtkrc-2.0 and add whatever font specs you desire. Mine looks like this:

```

gtk-font-name = "Tahoma 8"

```

Hope this helps someone.

---

