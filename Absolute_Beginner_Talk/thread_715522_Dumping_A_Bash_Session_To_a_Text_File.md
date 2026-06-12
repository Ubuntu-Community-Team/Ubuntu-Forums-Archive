---
title: "Dumping A Bash Session To a Text File"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by _crash_ on 2008-03-04
I want to save my Bash sessions to a text file.  (I am currently running Xubuntu 6.06.2 LTS).

In other words, while I am in the Xfce GUI, I start up Bash, do all kinds of stuff, and then close out Bash.  Then when I close out Bash, everything that I typed into the console and everything that the console displayed back to me will be saved to a text file.

I don't mind having to to invoke the name of a script file to begin and end the recording process.  The only problem is, I know nothing about Bash programming whatsoever.

Maybe there is some kind of plug in for Bash that will make this happen?  (Bash is extensible with plug ins, right?!?)

I am in the process of learning Bash, and having this feature available to me would help me immeasurably to get my act together.  I am sure it would help other Bash newbies out also.

Thanks to all in advance for any help!!!

Sincerely,


_crash_

---

### Post by PaulFr on 2008-03-05
My suggestion: When you start your terminal and are ready to start recording (both input and output), just issue the command ```
script mylog.txt
``` where **mylog.txt** is just a possible name for your log. When you are done, ```
exit
``` the bash shell. Every key stroke and output in that session will be recorded to mylog.txt.

---

### Post by kellemes on 2008-03-05
The following file holds your bash history.
~/.bash_history
Default this is set at the last 500 lines.
If you want to have more lines saved you can set the following variable in ~/.bashrc (for one user) or /etc/bash.bashrc (systemwide)
```

HISTSIZE=500

```

---

