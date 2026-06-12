---
title: "Terminal"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Stjames on 2008-03-24
This is kinda of dumb but i just downloaded realplayer and was tring to install it but i need to be able to access my home folder in the treminal folder.   So how do i move from folder to folder in terminal?

---

### Post by adult swim on 2008-03-24
im pretty sure the default setting in your terminal is the home folder
if that doesnt work for you type in, cd foldername, where foldername is the folder you are after.  
the default home folder is /home/username

---

### Post by williumbillium on 2008-03-24
a quick way to get to your home folder is:

```
cd ~
```

You can check where you currently are with:

```
pwd
```

---

### Post by kellemes on 2008-03-24
> **adult swim said:**
> 
the default home folder is /username/home

No it isn't.. the home folder = /home/<username>

---

### Post by Shazaam on 2008-03-24
```
cd
```
Change Directory. Like this....
```
cd /home/yourusername/.Trash
```
The dot (.) means its a hidden folder. To go back to the start if you want to  just type in.....
```
cd
```
To list what is in the directory type.......
```
ls
```

[http://www.linuxcommand.org/learning_the_shell.php#contents](http://www.linuxcommand.org/learning_the_shell.php#contents)

---

### Post by adult swim on 2008-03-24
> **kellemes said:**
> No it isn't.. the home folder = /home/<username>
woops! freudian slip! fixed!

---

### Post by Tyke91 on 2008-03-24
my sig has a handy link to a site where you can learn all about terminal commands, highly recommended :)

PS: why do you need realplayer to being with?

---

