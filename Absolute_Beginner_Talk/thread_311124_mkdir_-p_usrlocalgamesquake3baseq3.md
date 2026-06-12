---
title: "mkdir -p /usr/local/games/quake3/baseq3"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by fatneck on 2006-12-02
Hi all,

Trying to install Quake III Arena from this page:

[http://photoshopfreaks.com/index.php?id=129](http://photoshopfreaks.com/index.php?id=129)

and it won't let me do the "mkdir -p /usr/local/games/quake3/baseq" command. If I put sudo in front of it then it works, but then when I get to the end of the article and actually try to install the game, I get

"No write permissions on the install directory"

Do I need to change permissions on the directory, and if so how do you do that, or am I missing something obvious?

Cheers

---

### Post by LLRNR on 2006-12-02
Here's a quick general answer (you can apply it later on other concrete cases): if you need to change the permissions of a directory, go (**cd**) to the one above it (its "father") and do:```
ls -l     ["l" is lowercase "L"]
```You will see all the directories / files, preceded with a leftmost column of 10 chars: if the first char is a "d", it stands for "directory"; the next 9 chars (which can be "r", "w", "x", "-") mean the permissions to that directory / file. "r" is "read", "w" is "write", "x" is "execute" and "-" means no permission. They are grouped like this:

[rwx][rwx][rwx]

where the frist group represents the permissions for the user (u), the second is for the permissions for the group (g) and the third group is for others (o).

To change the permissions of a dir / file, use```

chmod *users***op***permissions* *file/dir*
```

where *users* can be "u","ug","ugo"="a","g","go","o",

**op** is "+" (add permissions) or "-" (remove permissions)

and *permissions* can be "r","w","x","rw","rx","wx","rwx"

Also, remember that in order to have access on a directory to **cd** through it, you need the "x" (execute) permission.

LLRNR

---

### Post by rdd on 2006-12-02
You should put a sudo in front of that mkdir and then allow all to run the program.

```
sudo chmod a+x /usr/local/games/quake3/quake3
```

Regards 

rdd

---

### Post by fatneck on 2006-12-02
Cool, thanks very much indeed. Will have a play with those settings and that should sort it out.

Cheers.

---

