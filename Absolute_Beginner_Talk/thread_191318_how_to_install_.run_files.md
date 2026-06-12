---
title: "how to install .run files?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-06-07
How do I install .run file?

---

### Post by Kilz on 2006-06-07
[QUOTE=mrvgarg]How do I install .run file?[/QUOTE]

Open the terminal, navigate to the directory the .run file is in and type 
sudo ./filename.run

---

### Post by mostwanted on 2006-06-07
run it :p

in a terminal:

```
/path/to/file.run
```

If it complains about permissions do:

```
chmod +x /path/to/file.run
```

---

### Post by mrvgarg on 2006-06-07
I tried and got this:

sudo ./et-linux-2.60.x86.run
sudo: ./et-linux-2.60.x86.run: command not found

---

### Post by rattking on 2006-06-07
i think that's a quirk with sudo could you try
sudo sh et-linux-2.60.x86.run

---

### Post by uzi09 on 2006-06-07
are you sure that's the correct name of the file?
also you want to make sure you're in the same directory as it too.

be sure that all the letters are capitalized where they're supposed to be and not in other places.

---

### Post by mrvgarg on 2006-06-07
Ok I have managed to install as user. When I open the folder I get some files. How do I now run it?

---

### Post by uzi09 on 2006-06-07
depends on what those files are.
try looking for a file called "README" or "INSTALL" and go through it. they usually give you instructions on how to get the thing running.

also just try calling the program name, or try it with "./" in front of it (ex: ./program)

if that still doesn't work, let us know, and we'll see then...

---

### Post by mrvgarg on 2006-06-07
Yes I got it working now. Thanks.

---

