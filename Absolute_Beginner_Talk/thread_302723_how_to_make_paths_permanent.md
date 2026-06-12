---
title: "how to make paths permanent?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by nite owl on 2006-11-19
Hi all, the usual 'export PATH=$PATH:*directory*' works great so I can run my scripts without having to type in the directory... How would I make this permanent??As everytime I go out of the terminal or log out I have to declare this again?? I read somewhere that I need to edit my .bash profile??? any1 know how to do this..

---

### Post by eeGhoong0ais on 2006-11-19
> **nite owl said:**
> Hi all, the usual 'export PATH=$PATH:*directory*' works great so I can run my scripts without having to type in the directory... How would I make this permanent??As everytime I go out of the terminal or log out I have to declare this again?? I read somewhere that I need to edit my .bash profile??? any1 know how to do this..


Your ~/.bash_profile contains a set of commands that are run every time you start bash [and so every time you open a terminal]. So, all you need to do is open ~/.bash_profile with your favourite text editor and add the command you've been typing to the end of it.

---

### Post by nite owl on 2006-11-19
> **Etiol said:**
> Your ~/.bash_profile contains a set of commands that are run every time you start bash [and so every time you open a terminal]. So, all you need to do is open ~/.bash_profile with your favourite text editor and add the command you've been typing to the end of it.
.....Where do i find my bash profile??????

---

### Post by Scorpuk on 2006-11-19
your .bash_profile is stored in your home directory.

ie username of john


/home/john


Since it starts with a .  the file is hidden.

Using a terminal window move to your home directory

```
cd /home/<username>
```

and type

```
ls -a
```

and you should see it listed there.

Now type

```
gedit .bash_profile
```

to edit it.

---

### Post by eeGhoong0ais on 2006-11-19
> **nite owl said:**
> .....Where do i find my bash profile??????


It's a file called .bash_profile in your home directory. In a terminal, you can refer to your home directory as "~", so typing something like ```
gedit ~/.bash_profile
``` would open it for you.

---

