---
title: "[SOLVED] easy question"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by christophdanger on 2007-08-04
[B]i need to move a file from my desktop to a directory, i can't just drag and drop it because i do not have the admin priviledges to do so.  how can i do this in command line?

man, i'm a newb.  but i gotta start somewhere! thanks everyone in advance.[/B] :guitar:

---

### Post by christophdanger on 2007-08-04
also, maybe there is a good command guide somewhere on the net that could help me get started?

---

### Post by Brunellus on 2007-08-04
open a terminal and

1) change to the desktop directory

```
cd Desktop
```

2) You can't do anything to the file (let's call it foo) becase you don't own it.  Luckly, if you are root (or have sudo privileges) you can change the file ownership easily.  If I (brunellus) were the user, then I'd go

```
sudo chown brunellus foo
```

which now makes me the owner of file foo.

3) move the file.  this is accomplished using the mv command.  this will move it to your home directory (~/)

```
 mv foo ~/
```

and we're done.

---

### Post by christophdanger on 2007-08-04
hey thanks alot worked great!

---

