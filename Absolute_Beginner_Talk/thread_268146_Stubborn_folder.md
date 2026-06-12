---
title: "Stubborn folder"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by thedivvyman on 2006-09-29
Hi  - I have somehow created a folder on the desktop (I think I created it when using cd/dvd burner) however it is empty and when I try  to move it to the wastebin I get an error saying   "Cannot move "/home/spik...sktop/dob" to the wastebasket because you do not have permissions to change it or its parent folder." I know its prob a simple operation but I am new to Ubuntu  and  not used to the terminal -  which is where I think you are going to send me.

Thanks in advance for any advice

---

### Post by bulldog on 2006-09-29
Use sudo and it will be gone,be sure you won't need it,it get's to the root waste basket.

---

### Post by thedivvyman on 2006-09-29
Bulldog - I said I was new  -  what is the code sudo remove "file?"
:confused:  embarrassed:confused:

---

### Post by Brownedwg89 on 2006-09-29
if its a folder use
```
sudo rm -r *foldername*
```

---

### Post by thedivvyman on 2006-09-29
Thanks  for that  -  job  done.  Could  you  just  explain  what  the  command  means?  I  do  really  want  to  learn  this  stuff.
Thanks  very  much

---

### Post by bulldog on 2006-09-29
> **thedivvyman said:**
> Bulldog - I said I was new  -  what is the code sudo remove "file?"
:confused:  embarrassed:confused:

So sorry,over looked it :D

Maybe this is of some use?

[http://gd.tuwien.ac.at/linuxcommand.org/index.php](http://gd.tuwien.ac.at/linuxcommand.org/index.php)

---

### Post by Famicommie on 2006-09-29
"sudo" means super user do, which is a method of performing root user tasks when not logged in as root. Think of it as being granted temporary administrator status.

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

If you want to learn more about using terminal commands, check out this guide:[http://www.linux.org/lessons/beginner/index.html](http://www.linux.org/lessons/beginner/index.html)

Some of the stuff is irrelevent to ubuntu, but I still learned an awful lot (I'm a new user, too :D )

To make sure that I could remember all of the commands, I opened up vi in the terminal and took notes on the stuff that I found to be most important. It didn't take me all that long to go through the course, and afterwards I found myself feeling much more comfortable.

---

### Post by Brownedwg89 on 2006-09-30
explanation of rm
[http://www.ss64.com/bash/rm.html](http://www.ss64.com/bash/rm.html)

---

