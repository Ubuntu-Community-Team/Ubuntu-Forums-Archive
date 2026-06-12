---
title: "[SOLVED] Remote Desktop file sharing?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Jareth on 2007-07-06
Howdy y'all!
I actualy still can't believe this worked in the first place but I can now work both my computers from one (I wish I could remember the person who showed me , thanks anyway!)

Now I was wondering if there is a way of using it to move files between computers, or do I have to use samba or NFS?

What I'm using is the VNC Terminal Server client (thingy) program that came instaled on Ubuntu in the first place. It works really well considering the age of the two computers, it goes through a router and one of the machines is wireless.

Is there anything else that can be done with this, that's clever and I haven't thought of yet?

Thanks muchly.

---

### Post by hyper_ch on 2007-07-06
For transfering files I'd use SSH...

You can setup the openssh-server on the linux box and then use WinSCP to copy from and to the linux box from your windows box...

---

### Post by Jareth on 2007-07-06
Sorry, forgot to mention they're both running ubuntu.

---

### Post by vanadium on 2007-07-06
There are several ways remote file systems can be mounted on your local machine, and thus be accessed as if it were local folders: nfs, sshfs, samba, ... this always involves installing the server in at least one point ( the one you will remotely access. Then, the shared directory can be mounted in the directory tree on the client side just as if it were a local folder.

This is what I followed for nfs: [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

This is what I followed for ntfsfs
[http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/)

---

### Post by Seisen on 2007-07-06
If its just between two Ubuntu computers use NFS from what I hear it is faster than Samba.

---

### Post by Jareth on 2007-07-06
okay, different prob.

Was 'messing' with ssh and have something on my desktop now which I've no idea how to get rid of
can anyone help?

Its the network folder icon, how to remove?

---

### Post by Jareth on 2007-07-06
Anyone?

---

### Post by Jareth on 2007-07-07
bump?

---

### Post by obrient on 2007-07-07
Right click on it and select unmount. That is the easiest way to do it.

---

### Post by Jareth on 2007-07-08
Brilliant! Thanks very much!

A nice clean desktop again!

---

