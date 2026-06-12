---
title: "i got this error when i installed feisty from hellanzb"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Malik on 2007-04-20
malik@malik-desktop:~$ hellanzb.py 
Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 14, in <module>
    from Hellanzb.Core import main
ImportError: No module named Hellanzb.Core



what do i do? :(

---

### Post by Seisen on 2007-04-20
Try putting python in front of the file and see if that works.

---

### Post by Malik on 2007-04-20
> **Seisen said:**
> Try putting python in front of the file and see if that works.
how do i do that? :(

---

### Post by Terl on 2007-04-20
> **Malik said:**
> how do i do that? :(

type:  python hellanzb.py

---

### Post by Seisen on 2007-04-20
type this in the terminal

```
python hellanzb.py 
```

---

### Post by Malik on 2007-04-20
> **Terl said:**
> type:  python hellanzb.py
malik@malik-desktop:~$ python hellanzb.py
python: can't open file 'hellanzb.py': [Errno 2] No such file or directory

---

### Post by Seisen on 2007-04-20
Are you in the same directory as to where you downloaded the file to.

---

### Post by Malik on 2007-04-20
> **Seisen said:**
> Are you in the same directory as to where you downloaded the file to.
before on edgy. I just opened terminal and typed in hella and then hit tab and enter and my download would start

---

### Post by Seisen on 2007-04-20
Go to /usr/bin/hellanzb.py and see if the file still exists or you have to redownload hellanzb.

---

### Post by Malik on 2007-04-20
> **Seisen said:**
> Go to /usr/bin/hellanzb.py and see if the file still exists or you have to redownload hellanzb.
what i found when i put in what u said

[http://tinypic.com/view.php?pic=2zhfo5t](http://tinypic.com/view.php?pic=2zhfo5t)


notice the other folder with the hellanzb-0.13 name

heres whats in it

[http://tinypic.com/view.php?pic=2cqjj1y](http://tinypic.com/view.php?pic=2cqjj1y)

---

### Post by Seisen on 2007-04-20
Try running it from the hellanzb-0.13 folder and see if it works.

---

### Post by Malik on 2007-04-20
> **Seisen said:**
> Try running it from the hellanzb-0.13 folder and see if it works.
how do i do that?

---

### Post by Seisen on 2007-04-20
```
cd whereverthefile 
``` in the terminal

---

### Post by Malik on 2007-04-20
aint work.

---

### Post by Malik on 2007-04-20
help

---

### Post by Seisen on 2007-04-20
Try redownloading and reinstalling hellanzb in feisty and see if that works.

---

### Post by sizzam on 2007-04-22
I was having the same problem with hellanzb installed from source on a fresh install of Feisty.   Here is how I fixed it:

hellanzb is now in the repositories.

First, I got rid of the copy of hellanzb that I installed:
```

$ sudo rm /usr/bin/hellanzb.py
$ sudo rm -rf /usr/lib/python2.5/site-packages/Hellanzb/
$ sudo rm /usr/etc/hellanzb.*

```
I then installed hellanzb from the repos.   Note that if you are doing a fresh install from the repos, you also need unrar and par2.

```
$ sudo aptitude install hellanzb unrar par2
```

I then executed hellanzb from a command line

```
$ hellanzb
```

and it worked.  After that, I killed hellanzb and configured it.   Note that your configuration file is now /etc/hellanzb.conf instead of /usr/etc/hellanzb.conf

Now I add this command to start hellanzb using screen whenever I log into Gnome:

```
screen -S hellanzb -d -m hellanzb
```

and I use this shortcut in Gnome to connect to that screen (make a custom shortcut with type 'Application in Terminal'):

```
screen -R hellanzb
```

---

