---
title: "Home directory acces whoopsie"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Crisps on 2007-12-10
I ran a chmod on my own user folder and now I have no access to it. (This should have given permission to everything in there to everyone I believe)

chmod 777 -R .

This did change the permission of every file as expected, but I do not have access to anything. The actual directory has x------xwr permissions. I am not sure why.

Now I cannot change the folder back. I cannot log in to that user account again as the startup scripts cannot even be accessed.

I do have access to all of the files from a different users account on the machine though. despite this do not have a way to change the user folder so that I have access.

sudo chmod 644 . does not do anything at all.

Any Ideas of how to fix this mess? I have the original ubuntu CD, is there a way I can use this to get into super user mode. And BTW, what happened to su on Ubuntu?

---

### Post by Dr Small on 2007-12-10
Boot up into recovery mode and then run:
```
chmod 644 -R /home/lockedoutuser
```

---

### Post by Pumalite on 2007-12-10
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

