---
title: "simple command line question"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by MrWashy on 2007-03-22
This is probably an incredibly newbish question, but how do I cd to a hidden directory in my home directory.  I'm trying to get used to using the command line but can't quite figure out how to do this.  

I tried to "man cd" but there's no man page for it!  I also tried "sudo cd" but sudo won't cd!

---

### Post by justleen on 2007-03-22
hidden dirs start with .

```
 cd .<yourdirname> 
```

ohw, and sudo cd wont work, cause you dont have to.
A user can cd to anydir, just wont be able to do anything there (/etc/ for example.. you can see everything, but cant change anything..)

---

### Post by 23meg on 2007-03-22
```
cd ~/.hiddendirectory
```

---

### Post by Bachstelze on 2007-03-22
As far as *cd* is concerned, there are no hidden directories, just type *cd name/of/dir*.

---

### Post by adam s on 2007-03-22
if you run the command 

ls -la

you will be able to see all the hidden directories

then just type

cd .directory_name

remembering to include the . (ie period) that is at the beginning of the hidden directory name.


Adam.

---

### Post by MrWashy on 2007-03-22
Wow!  Thanks for the fast replies!  That's got me moving now!

---

