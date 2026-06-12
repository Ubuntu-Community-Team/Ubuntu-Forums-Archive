---
title: "Bash Programming"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by pranaysatpalsharma on 2007-10-03
I am wanting to know how to create or spawn a process in Terminal window using a bash file code and executing it in terminal window. I know the use of commands gawk and echo, i know the if else structure but am unable to do it.I have looked up the code everywhere but it doesn't seem to work, the posix_spawn() and spawn() functions don't seem to work at all

---

### Post by dwhitney67 on 2007-10-04
I cannot understand from your post if it is a bash-script that you want, or if you are merely inquiring about how to run an application from the terminal (which is running a bash shell).

As far as a script is concerned, here is a simple application where a program can be started:

```
#!/bin/bash

# launch an application in the foreground
myProgram

# launch an application in the background
myProgram &
```

Of course, "myProgram" is merely an example.  You can substitute that for whatever program you are trying to run.

---

### Post by bodhi.zazen on 2007-10-04
??

You can spawn a sub-shell

(my_program &)

---

### Post by iconicmoronic on 2007-10-04
if you're in ubuntu default shell is bash, you shouldn't have trouble executing a bash script from the terminal without doing anything. are you typing correctly?

or like the man said, spawn a sub shell.

---

