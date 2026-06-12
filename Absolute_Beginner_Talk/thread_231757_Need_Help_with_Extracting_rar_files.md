---
title: "Need Help with Extracting rar files"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by nick_533 on 2006-08-07
how to extract multiple archived rar files :confused:

---

### Post by croak77 on 2006-08-07
Like test.rar.001 test2.rar.002?

---

### Post by nick_533 on 2006-08-07
no but file.part1.rar file.part2.rar

---

### Post by powder on 2006-08-07
Do you have the unrar package installed?

---

### Post by nick_533 on 2006-08-07
no i tried some stuff but it didnt worked :(

---

### Post by cantormath on 2006-08-07
> **croak77 said:**
> Like test.rar.001 test2.rar.002?

lol, what did you download of torrentspy?

open the folder and hit <ctrl>+2
look for the file that is just .rar
then extract that one....it will do the rest.

---

### Post by nick_533 on 2006-08-07
cantormath- i am not getting how to extract only :D

---

### Post by nick_533 on 2006-08-07
if i try to copy rar to /usr/bin it shows i dont have permissions to it :(

---

### Post by croak77 on 2006-08-07
> **nick_533 said:**
> if i try to copy rar to /usr/bin it shows i dont have permissions to it :(

You need to enable multiverse. If you  have Synaptic installed go here;

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

From the command line go here:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Once you have multiverse enabled, open a terminal and enter;

```
sudo aptitude update 
```
```
sudo aptitude install unrar
```

You should then be able to use any GUI archive app like file-roller, ark, xarchiver etc. Or you can use the command line.

```
unrar x /path/to/file.rar
```

---

### Post by mushroomcloudwarrior on 2007-12-15
I have Unrar installed already,

However, when i try to extract files that are in two parts;

file(part1).rar, file(part2).rar 

It somehow doesn't seem to know what to do!

---

### Post by h3rt3q on 2008-01-22
thank you. you saved my day..

---

