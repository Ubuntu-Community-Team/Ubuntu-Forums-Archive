---
title: "ls -d Not Working"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by navilon on 2006-07-24
i need to list just the directory contents of a folder and not its files

```
ls -d /home/navilon
```

returns

```
/home/navilon
```

and nothing else. Any ideas?

---

### Post by simonn on 2006-07-24
[QUOTE=navilon;1292433]i need to list just the directory contents of a folder and not its files
[quote]

File are the contents of a directory. :confused:

ls -d is working correctly.

What do you want to see?

---

### Post by orb9220 on 2006-07-24
When I ls -d /home/orb i get

orb@Two-Rivers:~$ ls -d /home/orb
/home/orb

orb@Two-Rivers:~$

If I just do ls /home/orb
Then I get the desktop folder there which is the only folder

---

### Post by FredB on 2006-07-24
man ls :

```

[...]
-d, --directory
              list directory entries instead of contents, and do not  derefer&#8208;
              ence symbolic links
```

---

### Post by OU812 on 2006-07-24
It's working the way it is designed to. Here's a link you may want to look at:

[http://www.computerhope.com/unix/uls.htm](http://www.computerhope.com/unix/uls.htm)

You could try this

ls -F /path

it lists folders and files, but flags folders with a slash (/).

john

---

