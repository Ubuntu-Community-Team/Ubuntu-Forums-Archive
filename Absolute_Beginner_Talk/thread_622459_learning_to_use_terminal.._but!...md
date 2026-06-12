---
title: "learning to use terminal.. but!.."
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by h-town on 2007-11-24
i'm following a guide from the forums and the very first thing it's showing me how to do is change directories. now this isn't exactly new to me since it's very similar to dos but  here is what happens:

harrison@loopy-logic:~$ cd desktop
bash: cd: desktop: No such file or directory
harrison@loopy-logic:~$ 


what's going on here? why can't i change directories? 

i'm sure this is a stupid question but i gotta ask them if i ever want to stop asking stupid questions.

---

### Post by nick_h on 2007-11-24
Files and directories are case sensitive in Ubuntu.

Try:
```
cd Desktop
```

---

### Post by Taboo Mirage on 2007-11-24
There are no "stupid questions."

The reason is because everything is case sensitive.  That is to say, "desktop" isn't the same as "Desktop".  To list the files and directories, use this:

```
ls
```

You will notice that the folder you want to change directory to is called "Desktop".  Therefore this will work for you:

```
cd Desktop
```

---

### Post by eggdeng on 2007-11-24
The directory is 'Desktop', everything in the terminal is case sensitive.

---

### Post by h-town on 2007-11-24
case sensitive... :lolflag:

thanks, it works

---

