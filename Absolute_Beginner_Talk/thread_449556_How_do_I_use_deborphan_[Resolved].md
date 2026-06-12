---
title: "How do I use deborphan [Resolved]"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by dunklegend on 2007-05-20
I want to use deborphan to get rid of the unused libraries.
What's the syntax to do it?
Is there a graphical way?

Thanks in advance

---

### Post by Kobalt on 2007-05-20
You can use deborphan directly from Synaptic, creating a filter. See [this]("http://ubuntuforums.org/showthread.php?t=140920") for more info. Beware though, deborphan can consider some packages such as video/audio codecs to be orphaned. Take a close look at what is listed before removing packages.

---

### Post by aysiu on 2007-05-20
*deborphan* has a graphical frontend called *gtkorphan*. If you install that, you can launch it with the command ```
gksudo gtkorphan
``` *apt-get* has a built-in feature that will remove unused libraries, too: ```
sudo apt-get autoremove
```

---

### Post by dunklegend on 2007-05-20
Thanks kobalt and aysiu, I just did what kobalt suggested and bookmarked that thread, and it cleaned a lot of stuff.

I'm going to write the commands that aysiu suggested in my Linux Setup document

Thanks a lot to both of you :KS

---

