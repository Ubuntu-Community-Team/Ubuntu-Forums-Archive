---
title: "installing .deb files"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-01-28
How do i go about installing a .deb file. i have downloaded it to my desktop but i realise now i have no idea what to do with it. If one of you lovely gurus can help me i can add another notch to my belt and go on to become the all powerful oracle of linux by the time i`m 412. 

   Thanks DK

---

### Post by jrib on 2006-01-28
assuming it will work in ubuntu, 

```
dpkg -i /path/to/file.deb
```

So if it's on your desktop:

```
dpkg -i ~/Desktop/file.deb
```

I would make sure it's not in the repos, and search the wiki/forums for other users' experiences with the particular program you are installing first however.

---

### Post by bigken on 2006-01-28
open terminal (applications/accessories/terminal)
change to super user (su)
cd to where you saved file ie cd Desktop
dpkg -i (name of package)
to change super user password type sudo passwd root 
then su:D

---

### Post by psomas on 2006-01-28
open the terminal...
switch to the directory in which you've downloaded the file and 
then write
dpkg -i filename.deb
(of course it might occur problems with the program's dependecies,and it might also affect system's stability)
check also this site: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

(edit: i didn't see the posts above)

---

### Post by DiscoKiller on 2006-01-28
Thanks everyone, you`ve been most helpful. forgot about the old dpkg -i command. never tackled a .deb file b4 u see. like giving myself (or rather everyone else) a challenge. Cheers again for the help...vegetable rights and peace x
         
DK

---

