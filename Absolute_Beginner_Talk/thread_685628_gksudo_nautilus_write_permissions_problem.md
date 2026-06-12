---
title: "gksudo nautilus write permissions problem"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by abyssius on 2008-02-02
I'm having a problem trying to gain write permissions on my system. While attempting to add some files to my /usr/lib/firefox/plugins directory, I first ran terminal and issued the command [gksudo nautilus]. the results are shown below:

[I]~$ gksudo nautilus
Initializing nautilus-open-terminal extension
Initializing gnome-mount extension
Initializing nautilus-image-converter extension

(gedit:6828): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/I]

It seemed to also trigger a debug log. I copied the line below from  nautilus-debug-log.txt:

[I]0x8177548 2008/02/01 16:30:13.9793 (USER): debug log dumped due to signal 11
0x8177548 2008/02/01[/I]

Apparently, I can't gain write permissions on any restricted directories. Anyone know what's going on?

-Thanks in advance from a determined newbie

BTW, I'm using Ubuntu Studio 7.10 which I installed over Ubuntu 7.10 Generic.

---

### Post by gn2 on 2008-02-02
Try Alt+F2 then gksudo nautilus in the window that opens.

---

### Post by jan quark on 2008-02-02
if you want to write into a restricted directory why not try

```
sudo cp /path/to/file /path/to/restricted/directory
```

this should copy the file into it

---

### Post by abyssius on 2008-02-02
Thanks jan quark and gn2:

FYI: I got the same results using the ALT+F2 and gksudo command. However, I was able to copy the files into the directory, using the [cp] command. This doesn't explain what's going on with gksudo nautilus, but I was able to achieve what I was trying to do. I'll continue to investigate.

---

### Post by Nythain on 2008-02-02
not sure if it makes a difference but try gksu instead of gksudo???

---

