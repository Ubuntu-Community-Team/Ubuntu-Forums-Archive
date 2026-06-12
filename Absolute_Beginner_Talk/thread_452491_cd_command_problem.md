---
title: "cd command problem"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-05-23
Hi folks,

I am struggling to learn linux.  I started with tutorials and then just started to do excercises to be sure I understood as I went.  So in my home directory I created some subdirectories.  one is linuxstuff and another is Open Office Files.  When I type cd linuxstuff, then linuxstuff becomes current.  cd ~ returns me to the home directory.  cd Open Office Files gives me no such file of directory.  then I type ls -l and it displays Open Office Files as a directory.  So I high light the Open Office Files printed with the ls command and paste it after the cd command.  But no luck.  Would someone please tell me what I should do to change to this directory.  I have stored files in this subdirectory using oo writer.

dace

---

### Post by taurus on 2007-05-23
The problem is that you have a space between Open and Office.  

Try

```
cd "Open Office"
-or-
cd Open\ Office
```

---

### Post by reckless2k2 on 2007-05-23
If I'm not mistaken, linux does not recognize spaces in the conventional manner or doesn' at all. Use and underscore (_) between the words and see if that gets you in. I think that's what I do.

---

### Post by wieman01 on 2007-05-23
Or do...
> cd Op
...and then press <tab> to complete the folder name. Tab gives you all option starting with "Op" in that case.

---

### Post by ICUR2Ys on 2007-05-23
Thank you

I tried the double quotes and that didn't work, I remembered something about using single quotes and that works fine.

Since the subdirectory was created with spaces the underscores do not work.

I really appreciate your help.

dace

---

### Post by ruy_lopez on 2007-05-23
Linux can handle whitespace just fine, its the bash shell, in fact, shells in general, which have idiosyncratic ways of handling spaces within names. The rule of thumb I use, if I'm going to access the folder or file from the command line at lot, I'll use "_" underscore in the name. On the other hand, if its a folder I'll access only from the GUI, spaces don't matter then.

Yes, the underscore only works if you created the file or folder with underscores instead of spaces.

---

### Post by brennydoogles on 2007-05-23
> **ruy_lopez said:**
> Linux can handle whitespace just fine, its the bash shell, in fact, shells in general, which have idiosyncratic ways of handling spaces within names. The rule of thumb I use, if I'm going to access the folder or file from the command line at lot, I'll use "_" underscore in the name. On the other hand, if its a folder I'll access only from the GUI, spaces don't matter then.

Yes, the underscore only works if you created the file or folder with underscores instead of spaces.

To add to that, it will make your life a ton easier if you always name with lowercase letters. That way you can use the autocomplete function of BASH without having to worry about whether or not the first letter is capital. Have fun!!

---

### Post by ICUR2Ys on 2007-05-23
Thank you wieman01  I tried your suggestion and that works too.  I like it alot because it saves me from making too many typing mistakes.

I really appreciate everyones help.

dace

---

### Post by Sparkster185 on 2007-05-23
I think you need a little crash course in how Bash (the shell) handles arguments.  When you execute a command and pass arguments, Bash handles each space separated string as one argument (unless you use quotes).  So when you say ```
cd Open Office Files
```, you are really passing *three* arguments to the cd command, not one.

---

### Post by ICUR2Ys on 2007-05-23
I am doing these excercises to be sure I understand.  And sure enough what I thought I understood because it is so simple, wasn't so simple.  Thank you all for helping me get a handle on this.

dace

---

