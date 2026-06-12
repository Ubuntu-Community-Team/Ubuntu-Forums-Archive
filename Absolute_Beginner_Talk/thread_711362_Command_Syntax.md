---
title: "Command Syntax"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by drubin on 2008-02-29
Hi guys

Not sure if this is a Ubuntu beginner question or a linux one?

I was asked to run this command 
```
find |wc -l
``` 

This got me thinking  i have seen symbols when running cmds. Is there a way that i can look up what they mean?

I am not exactly sure how to google "| &... ".

Is there a way i can learn how to run cmds/syntax/linux scripting?

Thanks

---

### Post by rbc on 2008-02-29
For general linux commands, I have found this site helpful:
[http://www.ss64.com/bash/index.html](http://www.ss64.com/bash/index.html)
Or, in terminal, type "man find" (without the quotes). Obviously, substitute "find" with whatever commands you want information about

---

### Post by kaens on 2008-02-29
[This guide]("http://tldp.org/LDP/abs/html/")

and "man bash" can help a lot - although it's a lot of reading.

The | is commonly called a pipe, by the way.

---

### Post by drubin on 2008-02-29
Thanks. But  the running of applications wasn't quite my questions, I do use man :) (that is a life saver!)

It was more the learning of "bash" syntax. I wasn't quite sure how to word my question 

Thanks. 
[The Guide]("http://tldp.org/LDP/abs/html/")  This looks like what i need, Just need to read through it 

Thanks guys.

---

### Post by es@urito on 2008-02-29
You should have a look at the bash documentation.
Bash is the most used linux shell and it give you the power of programming language. The easiest way to find info about bash syntax is the man pages
```
man bash
```
If you want to know more and see some examples try this:
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

Bash is a great glue to put together many simple and specialized tools like "cat" or "echo". The pipe (|) is used to use the output of a command, like "find" in your case, as the input for another command (wc).

Another similar example could be:
```
ls -l | wc -l
```
In wich you use the output of the "ls" command as input for "wc".

Have fun with bash!

---

