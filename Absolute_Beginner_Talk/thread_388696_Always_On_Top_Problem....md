---
title: "Always On Top Problem..."
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by qyte on 2007-03-19
For some reason xmms always on top does not function after a restart.
Could this be a gnome problem or xmms? xmms works very well after disabling and re-enabling always on top but doing that after every restart gets on my nerves after a while :(
I do not seem to know of any other app that has this option enabled though...

AND another thing that i do upon EACH AND EVERY restart...

sudo mount -t smbfs //qyte/music ~/Desktop/music

Is there a way to mount the damn thing automatically?

edit:
qyte is the network name for the windows pc ;)

---

### Post by simonn on 2007-03-19
Sorry can't help you on the XMMS thing, although this kind of thing should be handled by the windows manager, not the application - which probably explains why you havenot seen it much.

> 
Is there a way to mount the damn thing automatically?


Search on fstab and/or /etc/fstab.

---

### Post by blendmaster on 2007-03-19
While I too cannot help with XMMS at the moment (I haven't looked into it), maybe adding:

```
sudo mount -t smbfs //qyte/music ~/Desktop/music
``` 

to your list of startup programs might work (though I'm unsure of this for a fact).

---

### Post by mcduck on 2007-03-20
> **blendmaster said:**
> While I too cannot help with XMMS at the moment (I haven't looked into it), maybe adding:

```
sudo mount -t smbfs //qyte/music ~/Desktop/music
``` 

to your list of startup programs might work (though I'm unsure of this for a fact).
No, that wouldn't work. Using gksudo instead of sudo it would work, but it would ask you for password evey time you log in. 

The correct way to do this is to either add a line for it in /etc/fstab, or use the built-in network connection in Nautilus, in Places/Connect to Server. (I'd probably use the Connect to Server-way)

---

