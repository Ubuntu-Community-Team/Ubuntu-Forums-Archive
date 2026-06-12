---
title: "How do you run iPodPatcher in Terminal?"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Drunken Swagger on 2006-12-16
I'm trying to install Linux on my new iPod and I need to know how to run a command line program in Terminal. Any help?

-Drunken

---

### Post by tbroderick on 2006-12-16
What exactly are you installing? ipodlinux?

[http://www.ipodlinux.org/Installation](http://www.ipodlinux.org/Installation)

---

### Post by Drunken Swagger on 2006-12-16
> **tbroderick said:**
> What exactly are you installing? ipodlinux?

[http://www.ipodlinux.org/Installation](http://www.ipodlinux.org/Installation)

That doesn't have information on how to use Terminal, which is what I need.
Thanks for your help though.

-Drunken

---

### Post by tbroderick on 2006-12-16
What are you trying to run? Is it ipodlinux or rockbox?

---

### Post by jordanmthomas on 2006-12-16
applications -- accessories -- terminal

a few basic commands you'll probably need:
```
ls # prints current directorie's contents
pwd # prints current directory
cd *dirname* # changes to directory name dirname
./programname # executes program in current directory named programname
echo $PATH  # anything inside a folder this gives you you can run just by typing its name
```

So, to run iPodPatcher in a terminal if you have downloaded to your Desktop, you would do something like this
```
cd ~/Desktop # change to your Desktop directory:  ~ means "my home"
ls # see if your program is in here
./iPodPatcher # (or whatever the program is actually named)

```

Does this clear anything up?

---

