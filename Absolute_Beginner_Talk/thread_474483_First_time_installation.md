---
title: "First time installation"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by jrgibb on 2007-06-15
OK, so I've jumped in and made the change ! 

Installed 6.06 LTS yesterday on a box at home. First couple of questions; 

1) NTFS drives from windows, I can see the directories and can drill down but the actual files themselves are greyed out? is this a NTFS -v- Extended 3 problem or permission ?? 

2) I've installed AVG and when I go to update the virus definitions I get a "you don't have permission to execute" error ?

All help kindly received . . they'll be more stupid questions to follow ;)

J

---

### Post by Kobalt on 2007-06-15
Ubuntu doesn't come with read/write support for NTFS format, it only has read support. This is why your files are greyed. However, you can install [read/write support]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G") if you need to.
If AVG tells you that you don't have the permission to do this it's because you need to have root privileges to update the definitions. You need to launch AVG with root privileges then. You can try to do it this way : press Alt+F2 and enter ```
gksudo avg
```

---

### Post by Gannin on 2007-06-15
In Ubuntu 6.06, you can read from NTFS partitions, but you can't write to them.  There's no real need to have a virus scanner in Linux right now, but if you want to use AVG anyhow, and you want to update the virus definitions, the run it from the command line with the "sudo" command, such as "sudo avg" or whatever the command is to get AVG up and running.

---

### Post by jrgibb on 2007-06-15
Thanks guys, how do I setup root privileges for my default user id? 

Thanks,

J

Please ignore, have found details re sudo and the initial setup user.

---

### Post by hyper_ch on 2007-06-15
You already have those.... just enter "sudo" as first thing in a command to run it as root user

```

sudo avg

```

To run a graphical app as root:

```

gksudo ....

```

and the password it asks for is your user password :)

---

### Post by Kobalt on 2007-06-15
You might want to read a few things about root/sudo : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jrgibb on 2007-06-15
Thanks all ! 

I feel a new thread coming on . . . looking at an alternative to the media manager with my Streamium SLM5500.

Cheers !

---

