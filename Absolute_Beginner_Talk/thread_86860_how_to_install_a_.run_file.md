---
title: "how to install a *.run file"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-11-06
I recently downloaded a game with the file name:  alienarena-2006-x86.run.  The problem is that I don't know how to install this game.  Can someone tell me how to install this *.run file?

---

### Post by Xian on 2005-11-06
1. Open a terminal
2. cd to where the file is located

```
$ cd ~/
```

3. Make the file executable

```
$ sudo chmod a+x alienarena-2006-x86.run
```

4. Execute the file

```
$ sudo sh alienarena-2006-x86.run
```

---

