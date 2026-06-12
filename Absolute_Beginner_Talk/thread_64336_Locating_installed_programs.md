---
title: "Locating installed programs"
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by duke_nukem_time on 2005-09-10
I've installed a few programs on my computer from ubuntu universe, but when i go onto applications, they don't appear anywhere and I can't find their location or how to run the program.
Ex: openc++
I can't find it anywhere nor can i find info on how to load it.

---

### Post by mlomker on 2005-09-10
Look for it at a command prompt.

[b]sudo updatedb
locate[/b] filename

---

### Post by aysiu on 2005-09-10
Usually, you don't have to know the location of the problem. If it's installed, you can usually launch it by creating a launcher with the command *openc++*. If that doesn't work, open a terminal and type *man openc++* to see how you're supposed to launch it.

---

### Post by duke_nukem_time on 2005-09-10
[QUOTE=mlomker]Look for it at a command prompt.

[b]sudo updatedb
locate[/b] filename[/QUOTE]

I did that, but it would just return the same blank line i started with b4 i typed that in. I tried using command openc++, but it gave me the error:

Details: Failed to execute child process "openc++" (No such file or directory).

---

### Post by mlomker on 2005-09-11
[QUOTE=duke_nukem_time]I did that, but it would just return the same blank line i started with b4 i typed that in. I tried using command openc++, but it gave me the error:

Details: Failed to execute child process "openc++" (No such file or directory).[/QUOTE]

If it returns a blank line then it couldn't find it.  Try a less specific name, such as **openc**.

---

