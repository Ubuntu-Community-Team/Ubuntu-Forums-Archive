---
title: "[SOLVED] synaptic package manager problem"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-03-13
Im using Ubuntu 6.10 Edgy, i go System > Administration > synaptic package manager
I get nothing.. it doesnt load so dont other Aplications like Users & Groups, Is there a way i can sort of clean up the system.. like defrag?

Thanks, Davey

---

### Post by bollix47 on 2007-03-13
Try starting synaptic in a terminal window to see if any errors are displayed.

Applications - Accessories - Terminal

```
gksu /usr/sbin/synaptic
```

Linux uses a different file system from windows and doesn't really require defrag.  It will automatically check your disk every 30 boots using fcsk.

---

### Post by DaveyG on 2007-03-13
Thanks, but i get an error :( 

```
davey@davey-online:~$ gksu /usr/sbin/synaptic
sudo: must be setuid root
davey@davey-online:~$ 

```

---

### Post by Kateikyoushi on 2007-03-13
System > Preferences > Main Menu, then right click on the icon of the app and select properties, check whether the command starts with gksu.

---

### Post by DaveyG on 2007-03-13
Tried it in the terminal but still get an error...

---

### Post by Kateikyoushi on 2007-03-13
Boot into recovery mode and type this to terminal. Write down what's the output and let us know.

```
ls -l usr/bin/sudo 
```

---

### Post by bollix47 on 2007-03-13
Have a look at the 8th and 9th posts in [_this thread_]("http://ubuntuforums.org/showthread.php?t=228443&highlight=setuid+root").

8th post should read chown not chwon.

---

### Post by DaveyG on 2007-03-13
> Boot into recovery mode

Um hows that done? :confused:

---

### Post by Kateikyoushi on 2007-03-13
Restart and select recovery (singleuser mode) in grub.

---

