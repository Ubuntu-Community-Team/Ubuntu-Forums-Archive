---
title: "change default folder for ssh login"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Barleyman on 2007-04-16
I assume this is a simple question, but can't find a solution.

As I connect to a remote server via ssh, I would like to start in /var/www instead of /home/bill

Thanks in advance

---

### Post by finer recliner on 2007-04-16
o0o0o thats a new idea. i think i have an idea for you

log on to the remote server, and edit your .bashrc or .cshrc file (or whatever shell the server runs by default). at the bottom of this file type "cd /var/www" (without quotes). save the file. logout and then log back in and see if it works.


//your .bashrc file is autmatically run everytime you log on to the server. this is used for user specific settings. .cshrc (or any other shell config files) work the same way.

---

### Post by Barleyman on 2007-04-17
thanks finer,

It works like a charm.  I assumed I should change something in my .bashrc file, but did not realize I could just add a command at the bottom.  

I wasn't sure if your "oOoOoO" comment was sarcastic or not, but you solved my problem nonetheless.  Thanks again.

---

### Post by finer recliner on 2007-04-18
lol sorry, i wasnt trying to sound sarcastic. glad it worked for ya.

---

### Post by bashologist on 2007-04-18
Another solution that might work is:
```
ssh user@###.###.#.### cd /var/www
```

---

