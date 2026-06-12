---
title: "guides to executing programs/ installer"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by caffemusse on 2005-06-20
Just migrating from xp, I will probably post alot of stupid Q's.

Anyway, I would like to install firefox, and have downloaded (from firefox homepage) the file to /home/user .
How do I install the program / is there an installer that will start ? (I have already extracted the files...

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=caffemusse]Just migrating from xp, I will probably post alot of stupid Q's.

Anyway, I would like to install firefox, and have downloaded (from firefox homepage) the file to /home/user .
How do I install the program / is there an installer that will start ? (I have already extracted the files...[/QUOTE]


Look here:

[http://www.ubuntuforums.org/showpost.php?p=219789&postcount=8](http://www.ubuntuforums.org/showpost.php?p=219789&postcount=8)

What that doesn't cover, please ask questions about.

---

### Post by polo_step on 2005-06-20
[QUOTE=poofyhairguy]
What that doesn't cover, please ask questions about.[/QUOTE]
OK, so I went through all that uncommenting and soforth and...
[Later]
Reexamined the file and saw that I had modified it in a way I was told to in another message -- but I changed it all to the way the file on that page had it and it worked.

Still not sure what smeg did, but refreshing the panel brought up the programs I installed earlier.

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=polo_step]OK, so I went through all that uncommenting and soforth and...

anonymous@beatdown:~$ sudo gedit /etc/apt/sources.list

What's up with that?[/QUOTE]

You need to do more than uncommenting. You also need to add these lines to the sources.list:

> 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


---

### Post by blind0wl on 2005-06-20
Dont worry about smeg, just do a:

```
sudo apt-get install mozilla-firefox
```

Although you should all ready have firefox installed as part of the default installation of Hoary...

You cant find it in the Applications Menu?

---

### Post by polo_step on 2005-06-20
Did everything as you guys said and it all worked.  :)

---

### Post by polo_step on 2005-06-20
My only problem is that now I find that Seahorse only does GnuPG key management for some reason, and nothing else -- not even en/decrypt clipboard.  Something's not quite right there...I think there's more to the program than that.

Seems like it's supposed to integrate with Nautilus -- but how?

---

