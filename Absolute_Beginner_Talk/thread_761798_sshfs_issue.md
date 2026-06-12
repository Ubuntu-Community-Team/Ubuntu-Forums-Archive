---
title: "sshfs issue"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by Danikar on 2008-04-21
I followed the directions on Ubuntu guide to set up sshfs. 

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#SSH_Filesystem](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#SSH_Filesystem)

However when mounting the partition it gives me an error.
```
danikar@merek:~$ sudo adduser danikar fuse
Adding user `danikar' to group `fuse' ...
Done.
danikar@merek:~$ sudo mkdir /media/Remote\ Danikar/
danikar@merek:~$ sudo chgrp fuse /media/Remote\ Danikar/
danikar@merek:~$ sudo chmod 775 /media/Remote\ Danikar/
danikar@merek:~$ sshfs duser@dserver.com:/home/duser /media/Remote\ Danikar/
read: Connection reset by peer
danikar@merek:~$ 
```
At no point does it ask for my password. I figured it would ask for it after I used the sshfs command. But instead I got that.

Any ideas?

Thanks.

---

### Post by Danikar on 2008-04-21
Perhaps this shouldn't work at all but I figured I would try it.

I have openssh-server installed on my home machine, so I did the entire thing the same way and tried to mount a directory on my own computer through SSH.
```
danikar@merek:~$ sshfs danikar@localhost:/home/danikar /media/Remote\ Danikar
read: Connection reset by peer
```

---

### Post by Danikar on 2008-04-21
ROFL never mind.

I forgot I changed the port SSH is ran on.

---

### Post by bodhi.zazen on 2008-04-21
the sshfs error messages are often cryptic.

Try starting with a ssh connection. If that works, re-try sshfs.

My guess is a problem with known hosts, you could try deleting ~/.ssh/known_hosts and re-try sshfs, but that is just a guess.

---

### Post by bodhi.zazen on 2008-04-21
> **Danikar said:**
> ROFL never mind.

I forgot I changed the port SSH is ran on.

Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

