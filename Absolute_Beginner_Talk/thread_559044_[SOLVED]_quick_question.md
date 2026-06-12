---
title: "[SOLVED] quick question"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-09-24
to run a python script i use

sudo -sh (script location).py

right?

cause i forgot.

---

### Post by anemptygun on 2007-09-24
I don't know python, but from what I've read don't you just type

python file.py

---

### Post by rickycodie on 2007-09-24
i'll try it

---

### Post by rickycodie on 2007-09-24
no it doesn't work

---

### Post by rickycodie on 2007-09-24
wait.. i'm an idiot yea it works. thanks

---

### Post by anemptygun on 2007-09-24
Lol, thats ok.. glad I could help!:KS

---

### Post by 3rdalbum on 2007-09-24
To be more correct, you should make the Python script executable by giving it execute permissions in the Properties > Permissions tab. Make sure the Python script has:

```
#!/usr/bin/python
```

at the top of it.

Then, when you double-click the file you will be asked if you want to execute it or merely display it.

It is a security risk to run Python scripts that you don't know the origin of, that do not already have execute permissions applied to them. The same applies to shell scripts.

---

### Post by anemptygun on 2007-09-24
Ah \\:D/ looks like we got a pro!

---

