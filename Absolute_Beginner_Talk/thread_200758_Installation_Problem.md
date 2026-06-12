---
title: "Installation Problem"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-06-20
I just installed graphviz using the following in the terminal:

```
sudo aptitude install graphviz
```
However, the program wasn't added to the Applications menu and I cannot run it by typing "graphviz" into the terminal.  Does anyone know how to start this after it has been installed?

Thank you.

---

### Post by oyvindaa on 2006-06-20
[QUOTE=amcavoy]I just installed graphviz using the following in the terminal:

```
sudo aptitude install graphviz
```
However, the program wasn't added to the Applications menu and I cannot run it by typing "graphviz" into the terminal.  Does anyone know how to start this after it has been installed?

Thank you.[/QUOTE]

If you open the Alacarte Menu Editor, I think it's in the Graphics section.

I might be wrong.

---

### Post by taurus on 2006-06-20
Actually, it's in Applications -> Accessories -> Alcartte Menu Editor.

---

### Post by amcavoy on 2006-06-20
I can't find it there.  Did I use the correct command to install it?  I mean, it went through all of the steps as though it had been installed successfully, but I still can't find it...

---

### Post by user1397 on 2006-06-20
first of all, always make sure before you install a program, that you update aptitude/apt-get as such: ```
sudo aptitude update
sudo aptitude install <packagename>
```or to combine both, just type ```
sudo aptitude update && sudo aptitude install <packagename>
```

as for your program, follow my guide in my signature for "finding installed applications"

usually, you can just add a new entry in alacarte, and for the command use the same name as the package name.  for example, since you installed the graphviz package, the command would be **graphviz**. its that simple.

---

