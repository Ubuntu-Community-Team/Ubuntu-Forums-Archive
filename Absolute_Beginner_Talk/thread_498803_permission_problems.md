---
title: "permission problems"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by slimjim42 on 2007-07-11
I am a new user to both Linux and Ubuntu, i find it to a much better operating system than anything else out there, however i have messed some stuff up and i no longer have any permissions in my account. In the Gui i can no longer move/copy/edit any files nor can i download anything from the internet. 
I am using feisty fawn -64bit, and any help would be appreciated.

---

### Post by Inxsible on 2007-07-11
which folder exactly ?

Linux deliberately does not let users modify anything in any folders except their home. You can however, modify stuff if you assume the root privileges. On the terminal you can use sudo to assume root privileges

---

### Post by slimjim42 on 2007-07-12
it wont let me do anything on my desktop or in my home folder, And i tried setting the permissions on my user to have access to everything but it doesn't want to work for some reason

---

### Post by SyberKowboy on 2007-07-13
I'm having the same issue right now and have never expirenced this before. Any help please!

---

### Post by SyberKowboy on 2007-07-13
Found the answer! It's easy

```
sudo chmod -R 700 /home/<username>
sudo chown -R <username> /home/<username>
```

---

