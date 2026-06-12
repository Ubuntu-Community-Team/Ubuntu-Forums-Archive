---
title: "No GUI"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by lupgop on 2007-05-29
have i done somethingh wrong - i installed ubuntu server as intended host a basic website ??
does it come with a gui and i just did something wrong ??? i know where to get one i just want to know if i installed it correctly - as if i have not there may be other bits missing ...

---

### Post by Outrunner on 2007-05-29
Why would you use a gui for a server?

---

### Post by petersjm on 2007-05-29
Servers don't come with a GUI. You can install one, but there's little point. Pretty sure your install went correctly.

---

### Post by lupgop on 2007-05-29
so how do i access the cdrom drive so i can install the network card driver -- all the docs in documentation talk froim the point of view of  a gui ---  all i want to do is load a file of the cdrom ???
what the best book from the point of view of using a server - terminal entry ?

---

### Post by Outrunner on 2007-05-29
Well you can

```
cd /media/cdrom0
```

(change directory to /media/cdrom0 ) and

```
ls
```

(list files) and yuo should see your files from the CD. If it doesn't show any files then we'll have to mount the CD to see the files

---

