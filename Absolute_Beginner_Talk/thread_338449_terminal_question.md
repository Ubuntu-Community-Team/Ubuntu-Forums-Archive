---
title: "terminal question"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by valke on 2007-01-14
ok, having a little bit of issues navigating to the desktop in terminal. i am installing google earth, so if you could help a newb that would be awesome.:-k

---

### Post by taurus on 2007-01-14
You can use the cd command to move around from a terminal.  Otherwise, use nautilus then.

```
cd **directory_name**
```

---

### Post by IYY on 2007-01-14
So, in your case that's

```
cd ~/Desktop

```
or just

```
cd Desktop
```

if you are already in your home directory.

---

### Post by ewankho on 2007-01-14
I'm not sure what you mean by 'navigating to the desktop', do you want to go to the desktop directory? like: cd /home/<USERNAME>/desktop

---

### Post by finferflu on 2007-01-14
I'll just tell you a couple of basic commands:

ls - lists the contents of a folder, for example:

```
ls
```
Will list the contents of the current working directory

```
ls ~/Desktop
```
Will list the contents of the Desktop folder

to change into another directory

```
cd <location>

```
for example:

```
cd ~/Desktop
```
Will change into the Desktop folder.

To know in which directory you are working now, just type:

```
pwd
```
Even though you can usually see it from the prompt:
```
username@host:<current working directory>$
```

By the way ~ means /home/<your username>, and remember that linux is case sensitive, so ~/Desktop is different from ~/desktop.

Hope it helps ;)

---

### Post by valke on 2007-01-14
thank you all for your help!:KS

---

