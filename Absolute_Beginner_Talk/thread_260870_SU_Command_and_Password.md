---
title: "SU Command and Password"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by buzlink on 2006-09-19
I'm trying to run the SU command so I can install some programs from the command line.
I get an error message```
su: Authentication failure
Sorry.
```
The SU password is the same as my root password, correct?

Thanks

---

### Post by Irony on 2006-09-19
Use sudo as in;

[PHP]sudo mkdir /mnt/newfolder[/PHP]

See the Wiki for sudo.

---

### Post by aysiu on 2006-09-19
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by Irony on 2006-09-19
Yes that's the link.

Also if you want to run a graphical root program such as the Nautilus Browser use gksudo as in;

[PHP]gksudo nautilus[/PHP]

If you do sudo nautilus you may end up not being able to log in.

---

### Post by aktiwers on 2006-09-19
Or 

```

sudo su
```

---

### Post by Brunellus on 2006-09-19
```

sudo -s

```

And then use your USER password.

---

