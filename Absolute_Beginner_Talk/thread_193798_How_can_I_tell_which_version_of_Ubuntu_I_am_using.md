---
title: "How can I tell which version of Ubuntu I am using ?"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by bleakcabal on 2006-06-10
Well the title says it all I think : How can I tell which version of Ubuntu I am using ?

And I don't mean by checking my install disk. From Ubuntu how can I tell which version I am using ? I don't recall exactly which one I am using. I know I played with repositories and once I had a huge upgrade which changed the look of my desktop, my window manager verion, screen resolution, made sound not working, etc. 

The update was so drastic I am taking maybe I updated to another version.

---

### Post by SavageBeginner on 2006-06-10
In terminal: ```
lsb_release -ds
```

---

### Post by bleakcabal on 2006-06-10
Hum... seems I have updated to 6.06 LTS without my knowledge. Seeing as how this is the latest from the webpage and I downloaded a Kubuntu earlier than that must have been that large update.

The press releases does not mention which codename 6.06 LTS is. Is this the Dapper codename ?

---

### Post by SavageBeginner on 2006-06-10
Yes, Ubuntu 6.06 LTS is Dapper.  ```
lsb_release -c
```

---

### Post by Jucato on 2006-06-10
or ```
lsb_release -a
``` to see everything.

But you have it the other way around: Dapper Drake is the codename of Ubuntu 6.06 LTS (Long Term Support). :D

---

### Post by TravMan63 on 2007-06-14
Also
```
cat /etc/issue

```

[http://www.howtogeek.com/howto/ubuntu/how-to-tell-what-version-of-ubuntu-you-are-running/](http://www.howtogeek.com/howto/ubuntu/how-to-tell-what-version-of-ubuntu-you-are-running/)

TM

---

### Post by luke16 on 2008-05-20
What about 32 bit vs 64 bit Ubuntu? How do I tell which I am running?

---

### Post by joemacnz on 2008-05-20
If you don't know, then it is probably 32bit

---

### Post by luke16 on 2008-05-20
> **joemacnz said:**
> If you don't know, then it is probably 32bit

That's nice, but it doesn't really answer my question. Is there anyone who knows?

---

### Post by digitalvectorz on 2008-05-20
> **luke16 said:**
> What about 32 bit vs 64 bit Ubuntu? How do I tell which I am running?

[http://ubuntuforums.org/showthread.php?t=48393](http://ubuntuforums.org/showthread.php?t=48393)

---

