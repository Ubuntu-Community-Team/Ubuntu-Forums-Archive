---
title: "[SOLVED] Installing nvidia drivers"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by thenailedone on 2007-12-19
I am unable to get my [internet access]("http://ubuntuforums.org/showthread.php?t=639330") going at present in Linux so I downloaded the drivers from nvidia's website...

When I run the file it gives me an error and says I should shutdown the x-server first... so I read somewhere on this forum a while ago to press ctrl+alt+back space but that just takes me to the log on screen... how do I kill X...

And am I on the right track to finally getting my install to look pretty?



Cheers and thanks
Neil

---

### Post by kpkeerthi on 2007-12-19
You would need other 'dependencies' to get this going. See [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

To stop X, run in terminal
```

sudo /etc/init.d/gdm stop

```

---

### Post by thenailedone on 2007-12-19
> **kpkeerthi said:**
> You would need other 'dependencies' to get this going. See [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

To stop X, run in terminal
```

sudo /etc/init.d/gdm stop

```

:biggrin:

Thx for the link and for the assistance... I will try it when I'm back home...

---

### Post by thenailedone on 2007-12-20
...SUCCESS... lol

Ok, so after struggling for a while a finally realized the driver I downloaded was actually outdated and didn't support my gfx card (noob I am)... dl the latest driver and I'm in... no if I could just figure out how to get the enhanced desktop features going :( (but that is a problem for another thread :) )


Cheers
Neil

---

