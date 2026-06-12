---
title: "Installed Kubuntu Desktop: Konqueror Cannot Connect to Internet"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by bme on 2007-07-16
I installed kubuntu desktop on my ubuntu.
firefox can connect to the internet but konqueror cannot browse. It has an error like:

An error occurred while loading [http://www.google.com:](http://www.google.com:)
Could not connect to host [http://www.google.com/](http://www.google.com/).

What is the problem?

---

### Post by mendingo84 on 2007-07-16
are you under proxy? do you have a static IP? smth like this seems to be the problem. browse through the firefox config and you'll find out what's going wrong

---

### Post by bme on 2007-07-16
Oh I forgot to mention. If I sudo konqueror then konqueror can browse the net. Note no proxy and static IP.....I want to use konqueror as ordinary user

---

### Post by Difushion on 2007-08-25
Same problem here, any ideas?

I couldn't listen to Last.Fm radio streams with Amarok and with your "sudo" tip I can.

---

### Post by Grundlefleck on 2007-09-25
I had the same problem with Konqueror, couldn't connect to any host except when ran by root user. 

I went to Tools | HTML Settings and disabled cache and Konqueror could browse. The problem would happen again when I enabled cache so it must be something there.

~ Grundlefleck

---

### Post by crayzeewulf on 2008-04-30
> **Grundlefleck said:**
> I went to Tools | HTML Settings and disabled cache and Konqueror could browse. The problem would happen again when I enabled cache so it must be something there.

I experienced the same problem (after seven months since the above post) and the same solution works. However, the source of this bug is still not clear. Anybody have any ideas ?

Also see the following post:

[http://ubuntuforums.org/showthread.php?p=2236354](http://ubuntuforums.org/showthread.php?p=2236354)

According to this the problem is knetworkmanager. I confirmed that konqueror can connect to the internet after quitting knetworkmanager even when the cache is enabled.

---

