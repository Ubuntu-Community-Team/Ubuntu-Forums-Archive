---
title: "how do I move files with root privelages"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by irunwithknives on 2008-02-16
I just simply dont know how to move files with root privelages.

Help?

---

### Post by TheBoat on 2008-02-16
Most of those don't have to be moved but```
sudo mv *source destination*
```

---

### Post by st33med on 2008-02-16
I believe you do this in the terminal:
```
sudo mv <file> <directory to place it in>
```
to move the file or:
```
sudo cp <file> <directory>
```
to copy the file to a directory. Make sure it is a root file before you move it.

---

### Post by irunwithknives on 2008-02-16
thank you

---

### Post by spiderbatdad on 2008-02-16
Here'a a good guide to graphically moving files with root privileges. [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Here's a command line guide. [http://www.tuxfiles.org/linuxhelp/fileman.html](http://www.tuxfiles.org/linuxhelp/fileman.html)
This guide doesn't include the sudo command, so be aware moving system files would require you to prepend each of those commands with sudo. Or login as root with sudo su.

---

### Post by irunwithknives on 2008-02-16
thank you-much better

---

### Post by wolfen69 on 2008-02-16
> sudo nautilus
works

and having everything open in a new window can also speed up the drag and drop.

---

### Post by hyper_ch on 2008-02-17
if you want to do it through the cli, you also might want to look at midnight commander:

```

sudo apt-get install mc

```

and then run it with (or without sudo - depending on your needs)
```

sudo mc

```

---

### Post by aysiu on 2008-02-17
> **wolfen69 said:**
> works

and having everything open in a new window can also speed up the drag and drop.
Except you'd use ```
gksudo nautilus
``` instead of *sudo nautilus*

---

### Post by Sinkingships7 on 2008-02-17
> **aysiu said:**
> Except you'd use ```
gksudo nautilus
``` instead of *sudo nautilus*

why is that? when i was taught how to do it, i was taught to use gksudo also. but i used sudo once, and it worked exactly the same way. what's the difference?

---

### Post by aysiu on 2008-02-17
> **Sinkingships7 said:**
> why is that? when i was taught how to do it, i was taught to use gksudo also. but i used sudo once, and it worked exactly the same way. what's the difference?
Sometimes there is no difference, but it's a good habit to get into for when there is. More details [here](http://www.psychocats.net/ubuntu/graphicalsudo).

---

### Post by Faud on 2008-02-17
The difference is explained on this website.

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

