---
title: "Useful terminal commands for newbies?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Ki11ah on 2007-02-16
I am a Ubuntu n00b by a couple of weeks now and was wondering if it would be possible to have a sticky in beginner talk that lists some of the more useful terminal commands and what they do.

The reason I ask this is that I, and I am sure many other newcomers to linux have little or no experience in using the terminal/cmd and are pretty scared to do so. I think a list of common/useful commands would really go a long way into helping us understand a little more.

There is probably a list somewhere but I haven't seen one here and thought it would be ideal. You could call it 'Terminal Tips for Newbies' possibly :)

If there is one on this forum somewhere then maybe it needs to be a little more prominent.

Just a thought from a n00b.

---

### Post by ubu fubar on 2007-02-16
Something like [this]("http://css.engineering.uiowa.edu/tools/etudes/bash_shell.html")?

Just Google for "bash shell commands"...

---

### Post by highneko on 2007-02-16
In a terminal you can learn about any command with man.
```
man ls
man cd
man man
```
You could add ";" to these to make them one line:
```
man ls; man cd; man man
```
Good luck, have fun.

---

### Post by ubu fubar on 2007-02-16
> **highneko said:**
> In a terminal you can learn about any command with man.
```
man ls
man cd
man man
```
You could add ";" to these to make them one line:
```
man ls; man cd; man man
```
Good luck, have fun. 

Sure, but that assumes you already know the name of the command. If you don't know which command you need to navigate directories the man pages are pretty useless.

Type 'help' at the cli prompt.

---

### Post by Ki11ah on 2007-02-16
Thanks guys, some useful stuff there. Anyone got anymore?

---

### Post by highneko on 2007-02-16
Another note: Pressing tab twice allows you too see all available commands. And if you know some of the command you can type for example "cd" and tab twice will suggest the following:
```
highneko@ubuntu:~$ cd
cd                      cdrdao                  cdrecord.shm
cddb-slave2-properties  cdrecord                
cdparanoia              cdrecord.mmap           
highneko@ubuntu:~$ cd
```

---

### Post by zvacet on 2007-02-19
[http://www.ee.surrey.ac.uk/Teaching/Unix/]("http://www.ee.surrey.ac.uk/Teaching/Unix/")
[http://cypress.mcsr.olemiss.edu/unixhelp/commanz/index.html]("http://cypress.mcsr.olemiss.edu/unixhelp/commanz/index.html")

---

