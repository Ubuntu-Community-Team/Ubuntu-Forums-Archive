---
title: "rsync questions"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by phoenix24x on 2007-11-02
i am trying to set up a rsync server. after reading the tutorial [here]("http://everythinglinux.org/rsync/") it states that i should have certain files in my /etc directory, which i do not. i did 'locate' one the files and  
```
sudo cp /usr/share/doc/rsync/examples/rsyncd.conf /etc 
```

but there was no rsyncd.secrets file that is referenced in the tutorial. so i created it with VIM. is this going to be  problem later on?

---

### Post by shanepardue on 2007-11-02
Are you just trying to sync a couple folders or are you trying to do a more complex rsync? 
I learned everything I needed about it from the man pages and it wasn't very complex. 
Maybe I can help you if I know what you are trying to do.

---

### Post by mivo on 2007-11-02
There is also a nifty GTK frontend for it: [http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

If you ssh to another machine, the destination field looks like this: user@192.168.1.1:/home/user/backup-destination/

---

