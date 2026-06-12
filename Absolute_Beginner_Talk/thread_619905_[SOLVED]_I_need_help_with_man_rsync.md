---
title: "[SOLVED] I need help with man rsync"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-11-21
I am trying to figure this out. I run
```
tyler@tyler-laptop:/media/disk/DCIM$ rsync -t *.jpg tyler@tyler-laptop:/home/tyler/Test
```

the output is 
```
ssh: connect to host tyler-laptop port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [sender=2.6.9]
```

What am I doing wrong? I am trying to transfer from a thumb drive to a directory on my computer (Test).

---

### Post by torgrot on 2007-11-22
I certainly am not a bash expert, but reading the manual it would appear that the command should be rsync -t *.jpg /home/tyler/Test  If you put a colon in the either the source or destination it attempts to do the copies across the network.  So for a local copy you would leave out the user@host: part of the command.

torgrot

---

