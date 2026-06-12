---
title: "Error while installing updates using Synaptic"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by rbradshaw on 2007-09-24
While attempting to install new software updates, I received an error about dkpg, indicating that I must manually correct the problem I followed the instructions "dkpg --configure -a", but I don't think I am doing it correctly. The screen capture is attached.

Thanks
Randy

---

### Post by deadgobby on 2007-09-24
please open up the terminal anf input this command

sudo dkpg --configure -a

That should fix it


Gobby

---

### Post by rbradshaw on 2007-09-24
I entered the command as instructed. I received a "not found" error. Is there a specific directory I need to be in when running the command?

Randy

---

### Post by rsambuca on 2007-09-24
There was a typo!

Try entering ```
sudo [COLOR="Red"]dpkg[/COLOR] --configure -a
```

---

### Post by rbradshaw on 2007-09-24
thank you. sorry for the typo - my bad.

I received the following errors:

dpkg: error processing kdelibs4c2a (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up libvorbisfile3 (1.1.2.dfsg-1.2ubuntu2) ...

Setting up libvorbisenc2 (1.1.2.dfsg-1.2ubuntu2) ...

Errors were encountered while processing:
 kdelibs4c2a
rbradshaw@rbradshaw-laptop:~$ 

>> Do I need to reinstall dpkg? How?

---

### Post by Maestro23 on 2007-09-24
> **rbradshaw said:**
> thank you. sorry for the typo - my bad.

I received the following errors:

dpkg: error processing kdelibs4c2a (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up libvorbisfile3 (1.1.2.dfsg-1.2ubuntu2) ...

Setting up libvorbisenc2 (1.1.2.dfsg-1.2ubuntu2) ...

Errors were encountered while processing:
 kdelibs4c2a
rbradshaw@rbradshaw-laptop:~$ 

>> Do I need to reinstall dpkg? How?

Try:

> sudo dpkg --force-remove-reinstreq –remove kdelibs4c2a

---

### Post by ev5unleash1 on 2007-09-24
Yeah, I've had this problem in Ubuntu alot. So I tried Ubuntu Studio and did not get the problem and nor Edubuntu has this problem. I hope they figure out how this is happening and how exactly how to fix it and prevent it.

---

### Post by Pumalite on 2007-09-24
You can also try:

sudo dpkg --remove --force-depends --force-remove-reinstreq <packagename>

---

