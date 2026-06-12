---
title: "VLC media"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Tobster on 2006-09-16
How do I down load the VLC Media player it looks easy but i dont have a clue!

The page im looking at is:

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Thanks

Toby

---

### Post by Perfect Storm on 2006-09-16
Enable universe in your sourcelist then:

```
sudo apt-get update
sudo apt-get install wxvlc
```


Editing the sourcelist by command:
```
sudo nano /etc/apt/sources.list
```

save: <ctrl> + <o>
Exit: <ctrl> + <x>

---

### Post by shirilover on 2006-09-16
Another option is to follow the instructions here ->[http://nightlies.videolan.org/]("http://nightlies.videolan.org/")

This will install 0.8.5 as opposed to 0.8.4 which is in the universe repository.

---

