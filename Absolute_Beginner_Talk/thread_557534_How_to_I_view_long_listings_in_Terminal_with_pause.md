---
title: "How to I view long listings in Terminal with pauses?"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2007-09-22
Please allow me to explain my question better with more space... In a Terminal window, if I type a command that returns a huge heaping gob of text, it flies by too quickly to see.  And if it's beyond a certain number of lines, I lose the beginning and can't scroll up to it.  It's gone.

DOS had (for example) "DIR /P", which would list the current directory with pauses... hit a key and it would advance one screen at a time.

Is there some analog in Ubuntu's terminal, for commands like ls and others?  I've tried -p, --pause, etc., but to no avail.

If not, is there some way to remove the restriction on the number of lines buffered in the Terminal's memory, so I could scroll all the way up to the beginning regardless of how long the list is?

Thanks for any info you may have!

-Mark

---

### Post by Bothered on 2007-09-22
You probably want to pipe the output into a program that will do this for you - a pipe "pipes" the output from one program into the input from another, and is done with the character "|". As an example, to list a directory containing a large number of files, you can pipe the output of ls into a program called "less":

```
ls -l | less
```

Printing a screen at a time can be achieved using a program called "more", but this has (ironically) fewer features than less:

```
ls -l | more
```

---

### Post by vambo on 2007-09-22
```
<command> | less
```
You can then scroll up and down the page by page output

See

```
man less
```

---

### Post by mjpatey on 2007-09-22
That's a neat way to do it.  Of course, as in most things Linux, this is very modular!  So I assume one could even do:

ls | gedit

I will give it a shot when I get home tonight.  Thanks!!!

-Mark

---

### Post by Bothered on 2007-09-22
> **mjpatey said:**
> ls | gedit

Unfortunately that doesn't work - gedit doesn't accept standard input. However, you could use:

```
ls > files.txt & gedit files.txt
```

where ">" means "write standard output to" and "&" means "and then execute", although this is not as neat.

---

### Post by asmoore82 on 2007-09-22
> **Bothered said:**
> Unfortunately that doesn't work - gedit doesn't accept standard input. However, you could use:

```
ls > files.txt & gedit files.txt
```

where ">" means "write standard output to" and "&" means "and then execute", although this is not as neat.

small correction:
```
ls > files.txt **&&** gedit files.txt
```

``&&'' means ``**and** then execute''
``&'' actualy means ``execute in background [[and continue parsing command line]]''

---

### Post by mjpatey on 2007-09-22
Good stuff.  Thanks, everyone!

---

### Post by Bothered on 2007-09-23
Oops ... sorry about the typo

---

