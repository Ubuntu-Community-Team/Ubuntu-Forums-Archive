---
title: "Run a script??"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by natman on 2007-03-30
I am trying to install Maple11 on my machine, i have the cd rom and the, help file says to
" run installMapleLinux64"
I can see that file- and when the mouse is over it it says its a shell script.
I then bring up a terminal and type
[HTML]sudo ./installMapleLinux64[/HTML]
all i get is command not found. Im sure this is a real stupid question but can anyone tell me how to get the thing to start installing?

Thanks:

---

### Post by chili555 on 2007-03-30
A SHell script, eh? Let's try, first, making sure it's executable, and then installing it:```
sudo chmod +x installMapleLinux64
sudo sh installMapleLinux64
```Good luck and let us know.

---

