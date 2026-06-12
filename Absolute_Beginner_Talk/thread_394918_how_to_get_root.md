---
title: "how to get root"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by smurf killer on 2007-03-27
hi i am totally new to ubuntu and have just installed it tonight. i have played around with some other distributions but nothing seriously. but now i need some root permissions but i read somewhere that root password is disabled, and i guess that the entire root account is disabled then. how can i enable it again? i can't even get to root with the su command.?

---

### Post by Bachstelze on 2007-03-27
Enabling the root accound is not needed.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by smurf killer on 2007-03-27
thanks, not i know how to get to root. but i need to change the file /etc/apt/sources.list so i can add deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free can you help me with that, cause it is only root who have the RW permission

---

### Post by Bachstelze on 2007-03-27
You can do it the traditional way, using *sudo -i* instead of su, like this :

```
mfb@ana ~ $ sudo -i
Password:
ana ~ # nano /etc/apt/sources.list
```

or use sudo directly, like this :

```
mfb@ana ~ $ sudo nano /etc/apt/sources.list
```

If you want to use a graphical editor, gedit for example, use gksudo instead of sudo :

```
mfb@ana ~ $ gksudo gedit /etc/apt/sources.list
```

---

### Post by smurf killer on 2007-03-27
Thank you very much that couldn't have been better.

---

### Post by smurf killer on 2007-03-27
i thought i might quickly post here again. now i got the file changed but when i then use the command sudo apt-get update (the site i got it from is [http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)) the link times out. i really want the mp3 and other codecs, any idea how i do that?

---

