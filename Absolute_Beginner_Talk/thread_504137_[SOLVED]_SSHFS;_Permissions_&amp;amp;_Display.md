---
title: "[SOLVED] SSHFS; Permissions &amp;amp; Display"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Ek0nomik on 2007-07-18
I have never used SSHFS before, but I decided today that I wanted to try it out.

I followed this:  [http://www.go2linux.org/sshfs-mount-remote-filesystem-using-ssh](http://www.go2linux.org/sshfs-mount-remote-filesystem-using-ssh)

I am quite positive the directory is mounted with my surreal (my server) box.  I tried to delete the directory via sudo, and it said invalid permissions and started scanning through all the files on the surreal box.  So that leads me to believe that it is indeed mounted.

This was the command I ran to mount the directory:

```
dove@edelweiss:~$ sudo sshfs -p 2008 surreal@192.168.1.150:/home/surreal /home/dove/sshfs/surreal
```

The folder doesn't have any permissions now:

```
dove@edelweiss:~/sshfs$ ls -la
total 8
drwxr-xr-x  3 dove dove 4096 2007-07-18 18:27 .
drwxr-xr-x 66 dove dove 4096 2007-07-18 18:27 ..
?---------  ? ?    ?       ?                ? surreal

```

I presume you are supposed to be able to see the files via Nautilus with SSHFS?  If it isn't graphically, it would be redundant as you might as well use plain old SSH.

When I try to double click on the folder, I get this:  'Couldn't display "/home/dove/sshfs/surreal"' The attempt to log in failed.

If someone has any ideas, I'd appreciate it.  Thanks.

---

### Post by Ek0nomik on 2007-07-19
bump.

---

### Post by Ek0nomik on 2007-07-19
bump.

---

### Post by Ek0nomik on 2007-07-19
Removing 'sudo' from the command:

```
dove@edelweiss:~$ sudo sshfs -p 2008 surreal@192.168.1.150:/home/surreal /home/dove/sshfs/surreal
```

fixed the permission issue.

---

