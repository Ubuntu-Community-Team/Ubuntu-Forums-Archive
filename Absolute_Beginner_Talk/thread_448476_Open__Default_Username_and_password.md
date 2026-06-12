---
title: "Open  Default Username and password??"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by (aptainMorgain on 2007-05-19
Hey guy's (and gal's).

I'm trying to recover some data from a laptop using the open CD.

Booting up, accessing my HD works wonderful. :guitar::guitar: Even Sharing the folder seems
to be working - it automatically installs samba (from the web) and enables me
to share it on either windows or unix format.

Now, trying to access it from my desktop comes the tricky part - it asks me for
a user name and password.

ANY idea what the default open CD user name and password is for Ubuntu 7.04??

Anybody? :confused:

---

### Post by Najand on 2007-05-19
You mean the live CD? The User is Ubuntu and there is no password defined for it.... If you are looking for Samba user ID and password, you have to set a new username and password for it.

---

### Post by (aptainMorgain on 2007-05-19
Hey! Thanks for the quick response!

Yeah it seems I will have to do quite some setting up here before I can get this data transfered.
Where would I create samba passwords? I'm in over my head maybe :frown:

---

### Post by Najand on 2007-05-19
Open a terminal and run:
```

smbpasswd -a USERNAME

```
change USERNAME with your username and then enter your password.
You then need to restart samba.

---

