---
title: "Linux command question"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by b1g4L on 2007-05-04
I know the basics of wildcards, but I'm trying to figure out how to show all the files without a certain extension. For instance:

ls *.txt will show me all fies ending in .txt

I want to know how to find all the file in a directory not ending in .txt....



Also, what is the command to run an app but not stay "connected" to terminal?


Thanks.

---

### Post by jfinkels on 2007-05-04
> **b1g4L said:**
> I know the basics of wildcards, but I'm trying to figure out how to show all the files without a certain extension. For instance:

ls *.txt will show me all fies ending in .txt

I want to know how to find all the file in a directory not ending in .txt....



Also, what is the command to run an app but not stay "connected" to terminal?


Thanks.

You may want to use a program like grep and use a regular expression to govern the output of ls. For example, to use grep to show only files containing the word foo:
```

ls | grep foo

```

Type ```
man grep
``` for more information on grep.

And you can try typing the command followed by an ampersand like this:```
firefox&
``` This will allow you to run other commands in that terminal. however, when you close the terminal, firefox will close also.

More helpful to you might be the "Run Application" dialog. Press <Alt>+<F2>, then type the program you want to run.

---

### Post by davahmet on 2007-05-04
ls | grep -v <pattern to exclude>

For example, to exclude .txt files, "ls | grep -v .txt"

---

### Post by newlinux on 2007-05-04
You can also use the  bg (background) commands along with CTRL z

For instance:

```
gedit
```

hit control-z which will stop a job and then give you the job number, in this example, lets say it job #1

```
bg %1
```

then it is just as if you did gedit &. (this puts a job in the background).

Useful if you forget the &.

Also watch out for doing

```
sudo command&

```
if you haven't used sudo recently. In this case you will want to used the stopped job method above.

---

### Post by mostholy on 2007-05-04
thanks for the refresher course!  I've been away from linux for awhile and forgot some of the little things that used to be so easy. I think these things are useful for the newer folks just as I think that knowing some DOS commands comes in very handy at times (not to mention other shortcut keys and seemingly trivial keystrokes that can make or break your day). I guess I'm a bit taken aback at the prevalence of GUI approaches to tasks in linux these days (former SuSE 9.0 user).

Too many years without a CLI and I find I'm rusty.

---

### Post by jyba on 2007-05-04
You can do it without piping **ls** to **grep**:

```
ls --ignore="*.txt"
```

---

### Post by jfinkels on 2007-05-04
> **mostholy said:**
> I guess I'm a bit taken aback at the prevalence of GUI approaches to tasks in linux these days (former SuSE 9.0 user).

Well the command line approach is always going to be around for those of us who prefer it, but the goal for Linux is to make it so straightforward that even "your grandma" can use it (where "your grandma" is any average computer user :D ). That's why we are making things easier to use through GUIs.

---

### Post by jfinkels on 2007-05-04
> **jyba said:**
> You can do it without piping **ls** to **grep**:

```
ls --ignore="*.txt"
```

Even more elegant! Great, jyba.

---

### Post by abarth on 2007-05-04
> **b1g4L said:**
> I know the basics of wildcards, but I'm trying to figure out how to show all the files without a certain extension. For instance:

ls *.txt will show me all fies ending in .txt

I want to know how to find all the file in a directory not ending in .txt....



Also, what is the command to run an app but not stay "connected" to terminal?


Thanks.

Try this:

ls | grep -v '\.txt$'

To run a process in background use &. for example:

$ program & 

Cheers,
Alex

---

### Post by newlinux on 2007-05-04
> **mostholy said:**
> 
Too many years without a CLI and I find I'm rusty.

been there... still not as proficient as I used to be. But then, I guess I don't really have to be these days, but it's nice to know enough to know how to figure out things...

---

### Post by b1g4L on 2007-05-04
Thanks everyone for the quick, excellent advice. I appreciate the help.

---

### Post by josephus on 2007-05-05
you can also to use 

```
nohup gedit &

```

then even when terminal is killed gedit is still around.

---

### Post by hyperair on 2007-05-05
You can quit the terminal using the command "exit" after running a job with the ampersand and still have it stay up. However, if you click the X button on the window title bar instead of using the exit command, your task will close as well:

```
gedit & exit
``` will close the terminal and spawn a gedit window. This works in gnome-terminal, but I haven't checked with any others yet.

---

