---
title: "Your sesion lasted less than 10 seconds....&quot;  Cannont log into Gnome"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Yes on 2008-01-29
Whenever I try logging into Gnome I get the error "Your session lasted less than 10 seconds..." and in the details dropdown section it says something about "cannot create file _______: Permission denied".   The files are in my floder (/home/username), and I ran the commands 

```
sudo chown -R username:username /home/username
sudo chmod -R u+rw /home/alex
```

but I still get the error.

Last time I got this I was out of space on my root partition, what was the command that checks how much space you have?  I can log into the terminal but nothing else.

Thanks!

---

### Post by taurus on 2008-01-29
Is your log in name alex or username because the first command looks a little goofy to me?

---

### Post by Yes on 2008-01-29
Sorry, I meant to put username for that.

---

### Post by taurus on 2008-01-29
So your login name is alex.

```
sudo chown -R alex:alex /home/alex
sudo chmod -R 755 /home/alex
sudo chmod 644 /home/alex/.dmrc
```

---

### Post by Yes on 2008-01-29
Thanks, that seems to have done it.

---

