---
title: "Quick Terminal Question"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Sweet Mercury on 2007-05-21
I'm attempting to familiarize myself with Linux terminal commands, but I'm getting a strange error.

I have a folder which has a space in the name. The *ls* command will list the directory, but when I try the *cd* command I can't access it.

Here are my attempts:
```
mason@mason-laptop:~$ ls
bcmwl5.zip_FILES  Inuyasha manga                  uvsun_trace_big.jpg
Desktop           Sierra Madre - Leaves.mp3       WhereDoWeGo.mp3
Examples          Sierra Madre - Thorns.mp3
Films             sunset_a489_gamma_2sub_800.jpg
mason@mason-laptop:~$ cd Films
mason@mason-laptop:~/Films$ cd
mason@mason-laptop:~$ cd Inuyasha manga
bash: cd: Inuyasha: No such file or directory
mason@mason-laptop:~$ pwd
/home/mason
mason@mason-laptop:~$ cd /home/mason/Inuyasha manga
bash: cd: /home/mason/Inuyasha: No such file or directory
mason@mason-laptop:~$ cd Inuyashamanga
bash: cd: Inuyashamanga: No such file or directory
mason@mason-laptop:~$ cd Inuyasha_manga
bash: cd: Inuyasha_manga: No such file or directory
mason@mason-laptop:~$ 
```

Can the command prompt not access files/directories with spaces in the name?

---

### Post by nanotube on 2007-05-21
either escape the space with a backslash, or put the target directory in quotes.
```
cd Inuyasha\ manga
```
or
```
cd "Inuyasha manga"
```

for some more general terminal tutorials, check out linuxcommand.org :)

---

### Post by wormser on 2007-05-21
Try using a \ before the space.

```
cd /home/mason/Inuyasha\ manga
```

Another great tool in the terminal is the tab key.  Start typing in your command or directory location and hit tab, it will auto complete or give you a list of options.

---

### Post by freebeer on 2007-05-21
In the first example the "\" tells the command line interpreter that the next character should be included as part of the name.  So "My\ Documents" is interpreted as "My[space]Documents" and not as two names "My" and "Documents"  

It's probably in you long term best interest to avoid naming files with spaces.


Hope that helps some.

---

### Post by dbott67 on 2007-05-21
*[COLOR=Purple]EDIT:  Way too slow with the typing skills.  Pretty much what the folks above said! :)[/COLOR]*

There are 3 ways that I know of:

Suppose I want to access the directory called 'test dir':

1. Enclose the directory name in quotes:
```
dbott@feisty:~$ cd "test dir"
dbott@feisty:~/test dir$ 

```2. Spaces require an 'escape' character (the backslash '[COLOR=Red]\[/COLOR]') before the space to let the system know that the next character should be interpreted as part of the name:
```
dbott@feisty:~$ cd test[COLOR=Red]\[/COLOR] dir/
dbott@feisty:~/test dir$
```3. Use tab auto-completion:
Type in the first few characters of the directory and then press the TAB key:
```
cd test[COLOR=Purple][press TAB key][/COLOR]
```The filename (or command, whatever the case may be) should complete automatically:```
cd test\ dir/
```-Dave

---

### Post by Sweet Mercury on 2007-05-21
> **nanotube said:**
> either escape the space with a backslash, or put the target directory in quotes.
```
cd Inuyasha\ manga
```
or
```
cd "Inuyasha manga"
```

for some more general terminal tutorials, check out linuxcommand.org 

Yep, all those suggestions worked. Thanks--and to the others who replied as well. (I don't know why I didn't just try the quotes.)

I'm actually on linuxcommand.org walking through the tutorials, it's a great site!

Any other site suggestions?

---

### Post by jiminycricket on 2007-05-21
I think this is a wonderful GNU/Linux terminal walkthrough: [Linux Online - Getting Started with Linux: Table of Contents]("www.linux.org/lessons/beginner/toc.html")

---

