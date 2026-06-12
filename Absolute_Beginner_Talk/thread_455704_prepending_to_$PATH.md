---
title: "prepending to $PATH"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by cuberoot on 2007-05-26
Hi,

I am trying to prepend "." (current dir) to my path and I did:

set path=.:$PATH

when I source my .tcshrc and echo $PATH, I see "." in front of everything else and yet when I run an executable in my current directory, it does find it there automatically (without the ./).

How can I prepend "." to the path? Where is the default path variable set?

I'd appreciate any help. Thanks.

---

### Post by Stephen Howard on 2007-05-26
Putting the cwd at the start of PATH is a massive security risk.  Why do you want to do it?

If you must do it, put the cwd at the end of the PATH string not at the beginning.

---

### Post by cuberoot on 2007-05-28
Hello Stephen,

Why is prepending the path with cwd a security risk? Where is the default path set?  Thanks!

---

### Post by pmg on 2007-05-28
I agree, prepending . to PATH is unwise.  You never know when you'll be in a dir with it's own version of some command from /bin or /usr/bin, which could give unexpected results to commands you run or  are in other commands/scripts you run.  It would make it much easier to get you to run commands to don't intend to.  I think the security implications are pretty obvious.

But that doesn't answer the more general question of how to update PATH in (t)csh.  There are two kinds of variables in shells, environment variables and shell variables.  In (t)tcsh, you set shell variables with the **set** builtin command, and environment variables with **setenv**.  Also, by convention, shell variables are generally lowercase and env variables are generally upper case.  But, you can display both with **echo $*varname***.  If there is a shell variable with that name, it is displayed.  If not, but there is an env variable with that name it is displayed.  (**printenv** can be used to show env variables but won't show shell variables.)  So, **echo $path** shows the shell variable **path**, and **printenv PATH** shows the env variable **PATH**.

The shell keeps the shell variable **path** and the env variable **PATH** in synch.  Note that the format of the data in the two paths is different.   So, to set the dir /foo at the end of your path in csh you can do either of the following:
```
setenv PATH ${PATH}:/foo
   #or
set path=( $path /foo)
```
and it will set that variable and the shell will update the other one.

As for where the default path gets set, if starts with whatever is in /etc/environment and then goes thru the files listed in the tcsh man page under "startup and shutdown" (/etc/csh.cshrc, /etc/csh.login, ~/.tcshrc or ~/.cshrc, ~/.login and of course anything they in turn source like /etc/csh/login.d/*).  In general, environment variables are set in the "login" files not the "cshrc" files.

---

### Post by cuberoot on 2007-06-02
Thanks for the comprehensive explanation. Appreciate it.

---

### Post by preStop on 2008-03-15
This explanation was also just what I was looking for.  I wanted to "Thank" you, but I couldn't figure out how to do that officially.

---

