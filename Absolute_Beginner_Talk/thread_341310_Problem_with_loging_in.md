---
title: "Problem with loging in"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by ryn0 on 2007-01-18
I cant log in with usual account. It begins as normal, then switches to terminal then it returns back to gdm. it is still possible to log in as root. Before that i was making new partitions and stuff, might it be the cause?

---

### Post by Garyu on 2007-01-18
have you checked your /home directory to see that your home for your user is present and that it contains everything it should?

if everything is there, you should try to login as root (though usually this isn't recommended) and do
chown -hR username /home/username
this will make sure that your user owns everything in your home directory.
also, if this doesn't work, you might want to try
chmod -R 755 /home/username
this will change the rights of all files to read/write/execute for you and read/write for everyone else. maybe not the best solution, but if it gets things working you can limit rights later if you need to do so.

---

### Post by ryn0 on 2007-01-18
All the files in my home/user folder are accessible. I've tried what you said, but unfortunatelly it didnt work. Any other ideas?

---

### Post by Garyu on 2007-01-18
if you create a new user, is that user able to login and use the computer as normal?

you can try to rename .gconf (or .kde depending on what you are using). that way ubuntu will create new settings for your user. there might be something wrong in your user settings that needs to be corrected. don't delete this directory though in case you want to investigate what was wrong or restore old settings. just give it a new name, i.e.:

mv /home/username/.gconf /home/username/.gconf.old

---

### Post by ComplexNumber on 2007-01-18
> **ryn0 said:**
> I cant log in with usual account. It begins as normal, then switches to terminal then it returns back to gdm. it is still possible to log in as root. Before that i was making new partitions and stuff, might it be the cause?

when you say "partitions and stuff", what exactly is it that you did?

---

### Post by bapoumba on 2007-01-19
Your partition may be full.
From recovery mode :
```
df -h
```
will let you know. Make some room ;)

---

