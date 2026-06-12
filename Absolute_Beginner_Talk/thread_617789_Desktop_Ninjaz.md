---
title: "Desktop Ninjaz"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Joushlol on 2007-11-19
Ok, through some crazy circumstance, My desktop directory has been moved to my trash. I don't know how this happened. It could be just a slip of the mouse, or, like, a ninja or something. Because one minute i was rejoicing about finally installing cinerrela, and then this happens. Notice the confounding directories.
[[img]http://xs221.xs.to/xs221/07472/wtf_trash.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs221&d=07472&f=wtf_trash.png)

---

### Post by Billy_McBong on 2007-11-19
try 
```
mv ~/.Trash/Desktop ~
```

---

### Post by Joushlol on 2007-11-19
gah
```
joush@joush-desktop:~$ mv ~/.trash/Desktop ~
mv: cannot stat `/home/joush/.trash/Desktop': No such file or directory

```

---

### Post by Joushlol on 2007-11-19
srsly, this is annoying. i tried again as root, and from the destination directory. no cigar.

i'm sad. ='(

---

### Post by sc30317 on 2007-11-19
try the above command as sudo root

sudo **command**

---

### Post by crisnoh on 2007-11-19
Also, keep in mind that terminal commands are case sensitive.  If your trash directory is ".Trash", using ".trash" will cause terminal to attempt to manipulate a non-existent directory.

---

### Post by Billy_McBong on 2007-11-19
you have to use a capital T with .Trash
EDIT:crisnoh beat me to it

---

### Post by madestro on 2007-11-19
Also make sure you're using the command **exactly** as it's there. Unix terminal is case sensitive so you have to type

**sudo mv ~/.Trash/Desktop ~** then type your username password. Notice the capital letter in .Trash.

Hope this helps.

---

### Post by Joushlol on 2007-11-19
ok, i seem to have made a new desktop directory, but i still get this when i try to copy anything to the desktop.

[[img]http://xs221.xs.to/xs221/07472/Screenshot-1.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs221&d=07472&f=Screenshot-1.png)

now this happens :
```
joush@joush-desktop:~$ sudo mv ~/.Trash/Desktop ~
[sudo] password for joush:
mv: cannot move `/home/joush/.Trash/Desktop' to a subdirectory of itself, `/home/joush/Desktop'
joush@joush-desktop:~$ 


```

---

