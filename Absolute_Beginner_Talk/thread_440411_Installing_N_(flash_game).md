---
title: "Installing N (flash game)"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by jacob.neal on 2007-05-11
I'm trying to install a flash game called N ([[COLOR="Red"]link[/COLOR]]("http://www.harveycartel.org/metanet/downloads.html")). I have flash installed.

I've tried extracting the tar into my home folder. I wasn't able to run the executable there.
```
jacob@jacob-desktop:~$ cd n_v1linux
jacob@jacob-desktop:~/n_v1linux$ n_v14
bash: n_v14: command not found

```

 I moved it to /bin, and I wasn't able to run it there, either.
```
jacob@jacob-desktop:~$ sudo cp n_v1linux/n_v14 /bin
Password:
jacob@jacob-desktop:~$ sudo n_v14
n_v14: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

I'm pretty sure I don't have to move anything else in the directory, as it's all readmes and licenses. There is a file for additional levels, but I don't think the game requires them.

Thanks,
Jacob

---

### Post by Seisen on 2007-05-11
According to the readme it says to start the game the command is

```
nice -n 20 ./n_v14
```

if that don't work try 
```
./n_v14
```

---

### Post by jacob.neal on 2007-05-11
Thanks for the reply.

I'm not quite sure how I'm supposed to extract it. Right now the folder is in 
/home/jacob/n_v1linux

Both of the commands you gave me complain that there is no directory.

However, if I cd to the n directory, it gives me a different error.
```
jacob@jacob-desktop:~$ cd n_v1linux
jacob@jacob-desktop:~/n_v1linux$ nice -n 20 ./n_v14
./n_v14: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

Is   libgtk-1.2.so.0   something I need to install?

---

### Post by misterdog on 2007-05-24
i was getting the same error, looks like we are just missing a library

i just ran... 
$sudo aptitude install libstdc++2.10-glibc2.2
and then....
$./n_v14
and it started right up :p

---

### Post by madmatrixz3000 on 2007-10-25
Thanks that made it work

---

### Post by madmatrixz3000 on 2007-10-25
Okay now it will not play/interact.  Keyboard controls do not work

---

### Post by madmatrixz3000 on 2007-10-27
Does anyone know how to get the controls to work?

---

### Post by madmatrixz3000 on 2007-11-13
how do I get the controls to work

---

### Post by buddingh4x0r on 2007-11-20
k I got the same error.... however, when I ran 
$sudo aptitude install libstdc++2.10-glibc2.2
it did something but then it just threw up exactly the same error...
In other words, it didn't work.
any ideas?

---

### Post by buddingh4x0r on 2007-11-20
lol actually I just figured out an easier way to do it...
Just download the .exe version and then WINE it

---

### Post by madman91 on 2008-03-01
I too had many issues with the linux version, I simply used WINE as well.

---

