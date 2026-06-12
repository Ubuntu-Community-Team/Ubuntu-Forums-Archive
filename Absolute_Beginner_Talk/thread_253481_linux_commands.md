---
title: "linux commands"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by mikeee52 on 2006-09-08
I would like to know what command and the syntax for deleting a file or directory. I could not find it in linux commands.
thanks mike

---

### Post by Anonii on 2006-09-08
> **mikeee52 said:**
> I would like to know what command and the syntax for deleting a file or directory. I could not find it in linux commands.
thanks mike
rm <file>
rm -r <directory>


Check "man rm" for more info :]

---

### Post by BCRailrodder on 2006-09-08
Try rm /path/to/your/file  and rmdir /path/to/your/directory.

You can avoid typing in the paths all the time by using the command cd

cd /path/to/your/file.

Be very cautious when using the rm or rmdir commands as root because my understanding is once a file is gone.. it's gone for good.

A very good beginners site that I have found (which covers most of the basic commands is [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Good luck.

Kent

---

### Post by zxee on 2006-09-08
There's also the rmdir command for directories because linux likes lots of commands. > man rmdir

---

### Post by Omnios on 2006-09-08
Hi there is a link in my signature with lots of terminal command links

---

### Post by UltraMathMan on 2006-09-08
just an obligatory note of warning, by default rm doesn't confirm files it's deleting (ie. "Are you sure you want to delete...") so make sure the path is correct and you really want to delete the file or the directory and *all* the files contained therein.

---

### Post by Anonii on 2006-09-08
And I'll use an example to show you the DANGERS of using rm as root.

<rm -r ~/.wine/drive_c/blablagame/*>  
-You dont have the permission to do such thing
(This means I have to get on root! No problem!)

<sudo su>
(This will give me the root access for multiple commands, since I want to remove other directories and files after that. REALLY BAD HABIT FROM DEBIAN!!! NEVER USE SUDO SU :P, seriously... Why? Read after)

<cd ~/.wine/drive_c/blablagame>
-No such file or directory
(I didnt see that ^_^. I wasnt looking at the screen :P So the command got cancelled, and I went back to ~/)

<rm -rf *>
(hooray! I just deleted all my home directory, because I was a stupid retard who used sudo su, and the rm command without beeing careful.)


That was 5-6months before, when I was using Debian. In Debian I could use plain "su" but well, I translated to Ubuntu talk -> "sudo su".
And yes, its a real example :P That was the last time I used Debian, I tried Ubuntu after that and sticked with that :3

---

