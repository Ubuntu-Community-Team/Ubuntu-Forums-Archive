---
title: "Help with executables"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by Joelo on 2006-02-13
Hi everyone, ubuntu is my first linux expiernce, and so far I like it. How ever I can't get exectubales I think they are .runs to do anything. I start them and it says close, start, start in termanal I tried start and start in terminal and nothing ever happens. I am using the Debian distrubutions this is the correct ones right?

---

### Post by Jimmey on 2006-02-13
Try 
>  sudo sh nameofthefile.run  in the terminal.

---

### Post by wrtrdood on 2006-02-13
For most executables to work, shell script or otherwise, the x bit needs to be set on the file.  Do that with chmod +x <filename>

BTW:  I would not arbitrarily use sudo on just any file.  That's what it's there for.  To prevent running the system as root.  Try it first without being a super user unless specifically requested to do otherwise.

Another handy tool to help determine the type of file you're trying to execute is to use the file command.  For example:  **file** myfile
This will tell you what the file is - very handy.

---

### Post by Joelo on 2006-02-13
Help, it can't find the file. I am in home, and when I use the  ls and dir commands all I get is my usernames.

---

### Post by cwaldbieser on 2006-02-13
[QUOTE=Joelo]Help, it can't find the file. I am in home, and when I use the  ls and dir commands all I get is my usernames.[/QUOTE]
Type
```

$ cd

```
This will take you to your home directory.  That folder should be something like /home/joelo.

---

### Post by wrtrdood on 2006-02-14
Try *whereis <filename>* or *locate <filename>*

It's not in your path so you'll have to provide it.

---

