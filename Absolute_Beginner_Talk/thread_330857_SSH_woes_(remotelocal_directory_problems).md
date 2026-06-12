---
title: "SSH woes (remote/local directory problems)"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by noisc on 2007-01-03
I'm logging in to a remote machine with SSH. 

Be default, I start in my home directory on the remote machine. How do I change to a directory on my local machine? Suppose that my command prompt on the terminal of my local machine reads `me@my-computer:~'.  If I'm logged in somewhere else, I thought that ```
cd me@my-computer:~
``` should do the trick. But it doesn't. It just says the file/directory doesn't exist. How do I do this?

Also, very related, how do I copy files from local to remote? I thought something like ```
scp -r me@my-computer:~/files /destination
``` should do it, but again, the 'me@my-computer' part doesn't seem to reference my local directories. Help!

---

### Post by Dmole on 2007-01-03
this help?:
[http://ultra.ap.krakow.pl/~bar/DOC/ssh_backup.html](http://ultra.ap.krakow.pl/~bar/DOC/ssh_backup.html)

---

### Post by noisc on 2007-01-04
Hmmm, that link seems to be a list of commands for backing things up, which is indeed helpful for future reference, but I want to do something much simpler.

Basically I just want to know how to access my local file system in a terminal if I'm logged into another machine. I thought I could just do `cd me@my-computer:/', but that doesn't work. 

I've now figured out how to copy files using scp if I'm not yet logged in to a remote machine, but how do I copy files if I'm already logged into a remote machine?

---

