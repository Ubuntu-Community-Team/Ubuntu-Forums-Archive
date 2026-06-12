---
title: "tree"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-12-12
Hi

From drapper terminal I write 
> tree 
and I've got a:

command not found.
Thanxs for any hint

---

### Post by Iarwain ben-adar on 2006-12-12
EDIT:
read the posts beneath, and learned what it is..

Sorry for the comment :D


Iarwain

---

### Post by devnulljp on 2006-12-12
> **helphope said:**
> Hi

From drapper terminal I write 

and I've got a:

command not found.
Thanxs for any hint

First,make sure you have universe activated in /etc/apt/sources.list
(see here [http://ubuntuforums.org/showthread.php?t=3305](http://ubuntuforums.org/showthread.php?t=3305))
```
sudo apt-get update; apt-cache search ^tree
```
will tell you the name of the prog you want to install.
You should see output:
```
tree - displays directory tree, in color
```
So, now install it
```
sudo aptitude install tree
```
Once that's done, typing tree at the terminal should run it.

---

### Post by mcduck on 2006-12-12
that is because there is no such command. ;)

But if you want it, here's some info how to make one: [http://www.centerkey.com/tree/]("http://www.centerkey.com/tree/")

..or you can just use this one, although it's a bit hard to remember :rolleyes: 
```
ls -R | grep ":$" | sed -e 's/:$//' -e 's/[^-][^\/]*\//--/g' -e 's/^/   /' -e 's/-/|/'
```

---

### Post by helphope on 2006-12-13
Thanks everybody for answering.
I thought that the tree command was a built-in function.

> **mcduck said:**
> 
..or you can just use this one, although it's a bit hard to remember :rolleyes: 
```
ls -R | grep ":$" | sed -e 's/:$//' -e 's/[^-][^\/]*\//--/g' -e 's/^/   /' -e 's/-/|/'
```
I love this one; :D  :cool:  :) 
I'm trying to learn bash scripting,  grep and regexes; but all the tutorials to me sound too difficult.

thanks again

---

### Post by ciscosurfer on 2006-12-13
EDIT: already mentioned

---

