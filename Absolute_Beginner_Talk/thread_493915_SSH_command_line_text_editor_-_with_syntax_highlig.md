---
title: "SSH command line text editor - with syntax highlighting"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by theonlyalterego on 2007-07-06
I frequently find myself at work with a few minutes to kill, and often SSH into my home ubuntu box. For grins and giggles today I wanted to make some PHP changes to my site, but alas I'm stuck with the common command line editors, vi nano emacs. For the sake of argument lets say I want to do some development over SSH.

Is there a command line editor that has some sort of syntax highlighting? specifically for php. I googled and couldn't find anything =/

---

### Post by joselin on 2007-07-06
This is for **vim**.

```
$ cd
$ vi .vimrc
```Add the following:

```
syntax on
```Save and close. The open a php file... e voila!

---

### Post by Raineer on 2007-07-06
...

I didn't know that, now I need to learn vim lol

---

### Post by Cypher on 2007-07-06
Since you can SSH to your home machine, assuming you're running Windows at work, you can install Cygwin-X on it and then tunnel X through SSH and open up Emacs or other graphical editors..

---

### Post by theonlyalterego on 2007-07-06
> **joselin said:**
> This is for **vim**.

```
$ cd
$ vi .vimrc
```Add the following:

```
syntax on
```Save and close. The open a php file... e voila!

exactly what I was looking for, thanks!

@cypher - thanks I had explored some tunneling options, but I didn't know about that one. I'll check it out.

---

