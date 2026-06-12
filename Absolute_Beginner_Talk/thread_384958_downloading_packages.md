---
title: "downloading packages"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by igpar1 on 2007-03-15
Great application - install very smooth.

I am having problems downloading updates in both synaptic and via command line

The system has downloaded some packages but gets error messages at file 72 of 133.

Error appears to be with the au.archive.ubuntu.com.

See messgage below

Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources            
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release.gpg                              
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Translation-en_AU

Internet connection is ok with firefox and email.

Is the au server down?

Regards,

ian

---

### Post by AtrejuT on 2007-03-15
that seems to happen sometimes, and I don't really now why, though I had similar problems at one time as well.
You could either wait, see if it improves, or just try the main server (so same url without the au. part)
If you want to do that you have to edit a certain file which lists which servers to use: type
```

sudo gedit /etc/apt/sources.list

```
in a terminal, and adapt all the urls accordingly, don't change anything else.

good luck

atreju

---

### Post by igpar1 on 2007-03-15
Thanks for the reply.

I changed synaptic to point to the main server.

Downloading like a dream.

Many Thanks

Ian

---

