---
title: "gDesklets"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Tobywuk on 2006-10-20
having trouble installing gDesklets

I put this in to the terminal, but i get "couldent find package gDesklets

```


sudo apt-get install gDesklets


```
can anyone help? thanks

---

### Post by meng on 2006-10-20
Try gdesklets - case sensitive.

---

### Post by Tobywuk on 2006-10-20
i get the same thing. I nearly always have this problem. :(

---

### Post by Apotheosis on 2006-10-20
Why not just install it via the Synaptic Package manager or Add/Remove Programs?

---

### Post by taurus on 2006-10-20
Make sure you have both universe & multiverse enable in /etc/apt/sources.list.  Open a terminal and edit your /etc/apt/sources.list by removing the 3 sign in front of those lines...

```
gksudo gedit /etc/apt/sources.list
```
Then,

```
sudo aptitude update
sudo aptitude install gdesklets gdesklets-data
```

---

### Post by Tobywuk on 2006-10-20
when i put in gksudo gedit /etc/apt/sources.list, i get:

```

(gedit:10587): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


```

then i get a blank "sources.list" document up with nothing it in, just empty




EDIT- just successfully installed it through add programs GUI. but i would still like to know how i cant install this :(.   Also now i have the app, how do i make it show up on my desktop, and where is a good place to d/l them from?

---

### Post by taurus on 2006-10-20
That's just a warning and nothing to worry about it!  What is the output of this command, from a terminal then?

```

ls -la /etc/apt

```

---

### Post by dannyboy79 on 2006-10-20
> **Tobywuk said:**
> when i put in gksudo gedit /etc/apt/sources.list, i get:

```

(gedit:10587): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


```

then i get a blank "sources.list" document up with nothing it in, just empty




EDIT- just successfully installed it through add programs GUI. but i would still like to know how i cant install this :(.   Also now i have the app, how do i make it show up on my desktop, and where is a good place to d/l them from?

gksudo is for running GUI type application with root access. Gedit is not a gui frontend for anything, it's the actual program so if you wanted to be able to edit a file using gedit that was owned by root, you would simply use sudo gedit filename. only use gksudo for like nautilus. i may be wrong here but I don't think so.

EDIT: i just read all about this, I am wrong, check it out, [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Tobywuk on 2006-10-21
> **taurus said:**
> That's just a warning and nothing to worry about it!  What is the output of this command, from a terminal then?

```

ls -la /etc/apt

```

i get:

```

drwxr-xr-x    3 root root 4096 2006-10-20 19:43 .
drwxr-xr-x  100 root root 4096 2006-10-21 14:57 ..
drwxr-xr-x    2 root root 4096 2006-09-01 18:07 apt.conf.d
-rw-------    1 root root    0 2006-09-01 17:23 secring.gpg
-rw-r--r--    1 root root 2058 2006-10-20 19:44 sources.list
-rw-r--r--    1 root root 2003 2006-10-20 19:43 sources.list.save
-rw-------    1 root root 1200 2006-09-01 17:23 trustdb.gpg
-rw-r--r--    1 root root 2393 2006-09-01 17:23 trusted.gpg
-rw-r--r--    1 root root 2381 2006-09-01 17:23 trusted.gpg~


```

---

### Post by taurus on 2006-10-21
What do you mean your /etc/apt/sources.list is empty?  It is not from your output...

```

-rw-r--r--    1 root root 2058 2006-10-20 19:44 sources.list

```
So, try that command again or use nano if you wish!

```

sudo nano /etc/apt/sources.list

```
p.s.  Lower case letters are NOT the same as upper case letters since Linux/Unix is case sensitive...

---

### Post by podunk on 2006-10-21
The easy and fast graphical point and click way to enable extra repositories: [http://monkeyblog.org/ubuntu/videos/...positories.gif](http://monkeyblog.org/ubuntu/videos/...positories.gif) 
It's a little movie showing how to do it point and click style.

On the same page is a point and click tutorial on installing with the package manager (which is very easy and cool)
[http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic](http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic)

---

