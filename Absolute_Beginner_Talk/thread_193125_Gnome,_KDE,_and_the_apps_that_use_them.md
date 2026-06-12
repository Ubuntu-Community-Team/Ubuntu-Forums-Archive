---
title: "Gnome, KDE, and the apps that use them"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by Zikes on 2006-06-09
Total Linux n00b here, I've only had it for a few days but apart from a few problems here and there I'm loving it.  I've got Ubuntu 6.06 and use Gnome, and there are a few things that've been throwing me for a loop regarding Gnome & KDE.  I've seen a lot of programs made for KDE that I'd like to use, and I've heard told that it's possible to use (some of) them in Gnome, but I'm not sure what all that entails.

What are the possible consequences of using an app in a desktop environment other than the one it's made for?  Are they for the most part universal, with possible efficiency hits if run in an environment they're not optimized for?  If I were to install a KDE app and try to run it in Gnome would it run slower, not run at all, or potentially damage the OS?

Any clarifications on all this would be much appreciated :)

---

### Post by mostwanted on 2006-06-09
Not really any dangers. They just use a different graphics toolkit and other libraries for certain things. There are many different toolkits, even for Windows (gtk and qt exist for Windows too) and using another toolkit than the default one isn't really black magic. The only imprint you'll see will be on memory (several KDE libraries will have to be loaded).

---

### Post by Zikes on 2006-06-09
Ahh that makes sense.  So some of the more extensive apps would need more libraries from the other desktop environment, and running them would be the near equivalent of trying to run two desktops at once.

Very enlightening, thank you :D

---

### Post by aysiu on 2006-06-09
If you use a non-native application...

1. It will load up more slowly
2. It may look "ugly" or not fit in with the rest of your desktop theme
3. It may behave slightly differently, especially as far as drag-and-drop goes (it may, for example, move a file instead of copying it).

---

