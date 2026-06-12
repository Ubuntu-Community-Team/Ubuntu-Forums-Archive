---
title: "Setting a Variable to your PWD"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by blkhatpersian on 2007-07-30
hey, guys, how's it going? Got a simple question with setting a variable in csh. I want to set a variable to the present working directory (pwd), but so far I've had no luck with

set variable = pwd :P


Is there it can be done?

also it seems pwd/directoryname doesn't work with cd because I tried that as well.

Any help would be appreciated! :popcorn:

---

### Post by bren on 2007-07-30
most variables are of the form $VARIABLE

dont know if this will work with $PWD

try?

bren

---

### Post by pmg on 2007-07-31
The convention is to use uppercase for environment variables and lowercase for shell variables, but nothing enforces that.  I think csh sets the environment variable PWD to the current working directory, so you could use that, or to set your own shell variable you could use:
```
set mypwd=$PWD
```
If for some reason $PWD isn't being set, you could also run the pwd command and put it's result in a shell variable with:
```
set mypwd=`pwd`
```

---

### Post by blkhatpersian on 2007-07-31
Awesome, the first line worked! THANKS! :guitar:

---

