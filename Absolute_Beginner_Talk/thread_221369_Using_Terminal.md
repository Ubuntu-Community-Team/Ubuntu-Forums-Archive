---
title: "Using Terminal"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by Caraethelanea on 2006-07-23
How do I open a file (text) using terminal?

Thanks.

~Carae

---

### Post by bruenig on 2006-07-23
First, terminal is located at Applications>Accessories>Terminal if you didn't already know.
to open the file in the terminal you do
```
nano /path/to/file
```
or
```
vim /path/to/file
```
obvioiusly replacing the appropriate parts
if you mean open a file with the terminal as in with a seperate program
```
gedit /path/to/file
```
If you intend to change the file, you may have to add 'sudo' before those commands.

---

### Post by OU812 on 2006-07-23
And if you need to edit the file, just precede any of the given commands with sudo.

john

---

