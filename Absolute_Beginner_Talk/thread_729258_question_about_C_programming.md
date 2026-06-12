---
title: "question about C programming"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by thungmail on 2008-03-19
I would like to know why we have to have"./" in order to execute the C code in Ubuntu. I remember in my university, I dont need to type "./" to execute. Can anyone here explain to me.
Thanks

---

### Post by (((X))) on 2008-03-19
./ means>run in terminal, or am I wrong?

---

### Post by p221072 on 2008-03-19
If you write some code in C, you will need to compile it using gcc before executing it.
When you have an executable file writing './' before the name of the file you mean that the command is in the current folder instead of the default /bin folder were the executable normally stay.
Hope this helps...

---

### Post by Oldsoldier2003 on 2008-03-19
> **(((X))) said:**
> ./ means>run in terminal, or am I wrong?

(./) is the path so that your shell gets it right. if the directory is already in your path environment you can just type the scriptname

---

### Post by thungmail on 2008-03-19
Yeah It is clear now.

---

### Post by The Cog on 2008-03-19
It's nothing to do with C code. It's all to do with your path. In DOS and windows, your current directory (.) is in your path, meaning that it is searched when a command is entered. In unix and linux, the current directory is not in your path, so you must tell the command interpreter where to find the command you want to run, e.g. /opt/ut2004 or if it's in the current directory, ./prog-name. This applies to any executable, be it compiled program or a script.

You can see your path with the command
```
echo $PATH
```
and you can add the current directory to the path (thus avoidig having to type ./ with
```
export PATH=$PATH:.
```

---

