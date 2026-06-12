---
title: "shell variables/echo/export - not working as expected"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by cheber on 2007-06-23
This works:
$MYNAME=cheber
$echo $MYNAME
cheber

According to the book, it shouldn't work when starting a new shell:
$MYNAME=cheber
$echo $MYNAME
cheber
$bash
$echo $MYNAME
(empty line)
$

But for me it works without using export. Why?

If I DO use export (or without) and login as another user it won't work.

---

### Post by Pragmatist on 2007-06-23
Please post exactly what you type into the terminal.

I tried this and everything worked as expected:

> 
desktop:~$ MYNAME=me
desktop:~$ echo $MYNAME
me
desktop:~$ bash
desktop:~$ echo $MYNAME

desktop:~$ 


---

### Post by cheber on 2007-06-24
Ok, this is weird.
I works as it should now for some reason, and I _know_ I did it exactly same way last time. I tried like 10 times. Ah well.

But I still can't get it to work if I login as another user. If I set a variable in "shell A" as user "cheber", shouldn't also user "test" in "shell A" have access to the variable?
Or I'm not in same shell when switching users?

Even if I use export it won't work with other users.

edit:
One more thing. How do I remove a "readonly" setting on a variable?

---

### Post by Pragmatist on 2007-06-24
There is no problem, you just need to do some more reading about the shell.  There are many excellent, and free, tutorials out there.  Just use google and you will find them.

In the meantime, here is a simple explanation:

A shell is just a *program*.  There are many shell programs (i.e. bash, csh, tcsh, zshell, and so on...)  You could even install some of these other shell programs from the repositories if you want.

Most programs have user configuration files that define the preferences of a specific user.  These are usually found in the user's home directory as "hidden" files.  They can be viewed by using the **-a** switch to the **ls** command:
```
ls -a
```In addition to a user configuration file, most programs have a "default" configuration that will apply to any user.  For example, firefox has default bookmarks and Open Office Writer has default settings for a plain document.  Default files for system programs are usually found in **/etc ** The defaults for other programs are usually found in the users home directory as "hidden files".  
The program called bash has defaults in /etc and in hidden files in the user's home directory.

What is the point of this explanation?  Well, whenever a particular user starts a program, she gets a default configuration.  If the user makes any changes, those changes are **just for that user**.  For example, if you add bookmarks in firefox, those will only be there for you.  If you login as another user, you will get the default bookmarks.  You could copy the bookmarks file from one user to another and then you would have the same bookmarks for both users.

The user configuration files for bash can be found using this command:
```
ls -a | grep bash
```The output should look something like this:
> 
desktop:~$ ls -a |grep bash
.bash_aliases
.bash_history
.bash_logout
.bash_profile
.bashrc
desktop:~$ 
Take a look at **.bashrc**  You will find lines like this:
> 
# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
This line sets the HISTCONTROL variable for your user.  What does export do?  Here is a quote from this tutorial: 

[http://www.debian.org/doc/manuals/debian-tutorial/ch-shell.html](http://www.debian.org/doc/manuals/debian-tutorial/ch-shell.html)

> **export** means to move the variable from the shell into the environment.  This means that programs other than the shell will be able to access it.Remember that the shell is just a program.  So when you run **bash** you are running another "instance" of that program.  This would be true if you opened a word processor like oowriter and started typing a document, and then you ran oowriter again without closing the previous one.  The second oowriter instance would have a blank document, not a copy of the document you are already creating.  When you use export, "programs other than the shell will be able to access it."  This means any program, including another instance of bash.

Each user has his own environment, that is why your your export as cheber didn't work for the user called test.  When you export, you make a variable accessible to any program in your environment.  Another user has a different environment, and won't have that variable.

If you want a variable to apply to all users, you need the **/etc/profile** configuration file.  As I wrote eariler, bash has a user configuration file and a system configuration file.  /etc/profile is the system configuration file.  You can only modify it as root.  Be careful making changes to this file!

**edit:** In this explanation I used the terms "program" and "instance".  Normally, the term "process" is used rather than "program" as it is more accurate for this kind of discussion.  "Bash" is a program.  A particular instance of bash running is called a "process".  To see this, run bash a few times in a terminal (or open gnome-terminal several times--each time gnome-terminal runs it starts an instance of bash).  Then, use the **ps** command to see a list of the processes:
For instance:
> 
desktop:~$ bash
desktop:~$ bash
desktop:~$ bash
desktop:~$ ps -ef |grep bash
me     5873  5837  0 07:39 pts/0    00:00:00 bash
me     6406  5873  2 09:07 pts/0    00:00:00 bash
me     6422  6406  3 09:07 pts/0    00:00:00 bash
me     6438  6422  4 09:07 pts/0    00:00:00 bash
me     6455  6438  0 09:07 pts/0    00:00:00 grep bash
desktop:~$ 
Note that there are four bash processes running.  The first is the process created when I opened gnome-terminal.  The next 3 processes are the ones I started by typing "bash".  Because a shell is a program used to run other programs, this can be confusing.  At this stage, I am in a subshell, within a subshell, within a subshell.  Let's see the process tree:
> 
desktop:~$ ps f |grep bash
** 5873 pts/0    Ss     0:00 bash**
[COLOR=Blue] **6406 pts/0    S      0:00      **....**\_ bash**[/COLOR][B]
 [COLOR=Red]6422 pts/0    S      0:00                [/COLOR][/B][COLOR=Red]..........[/COLOR][COLOR=Red].[/COLOR][B][COLOR=Red]\_ bash[/COLOR]
[COLOR=DarkGreen] 6438 pts/0    S      0:00                          [/COLOR][/B][COLOR=Black]..................[/COLOR]**[COLOR=DarkGreen]\_ bash[/COLOR]**
         6544 pts/0    S+     0:00 .......................\_ grep bash
desktop:~$

(note: I inserted the periods to keep the visual hierarchy you'd see if you typed this in a terminal.  For some reason the forum here doesn't preserve white space.)   I'll refer to the different bash processes by color.  Black is the process started by gnome-terminal.  Blue is a subshell to Black, Red is a subshell to Blue, and Green is a subshell to Red.  "grep bash" is a process begun in the "green" subshell.  Every process has a "parent".  In this case, Green's parent is Red, Blue's parent is Black, etc...etc...
To get out of these nested subshells, I could use the "exit" command:
> 
desktop:~$ exit
exit
desktop:~$ exit
exit
desktop:~$ exit
exit
desktop:~$ 
If I type exit a fourth time, I will exit from gnome-terminal.

---

