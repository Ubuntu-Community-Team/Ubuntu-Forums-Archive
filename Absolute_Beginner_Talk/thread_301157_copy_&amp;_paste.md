---
title: "copy &amp; paste?"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-16
Probably a silly question: But I do not seem to be able to simply copy files and paste them in certain folders of the filesystem, I guess this has to do with permissions?

I have downloaded some brushes for Gimp, I would like to copy them to /usr/share/gimp/2.0/brushes

I tried selecting them and copying them. But the 'paste' option cannot be selected once I am in the 'brushes' folder.

---

### Post by echo $USER on 2006-11-16
Try it from the terminal as root...
> 
sudo cp -rf what_to_copy where_to_copy

---

### Post by PartisanEntity on 2006-11-16
Well I managed to copy the folder to /usr/share/gimp/2.0/brushes but the brushes still will not show up in Gimp. I need to copy the brushes out of that folder and into the brushes folder of Gimp.

There are too many to use that command over and over again. Any other way?

---

### Post by aysiu on 2006-11-16
Any other way? Yes. Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by LLRNR on 2006-11-16
Here's my idea: make an empty folder where you then put all the brushes you need. In order for this to be easier, just create it on the desktop. In a terminal type (assuming you called this folder "Brushes"):

```
cd ~/Desktop/Brushes
sudo cp * -r /path/to/where/you/want/to/put/the/brushes
```

HTH,

LLRNR

---

### Post by echo $USER on 2006-11-16
Do it recursively, so you only have to type the command once...

> sudo cp -rf /brush/folder/* /where/to/copy

/brush/folder/* means it will copy all the files in that folder to /where/to/copy.  Don't forger to leave out teh -rf (recursive, force).

---

### Post by PartisanEntity on 2006-11-16
Thank you all for the tips and for the link, good site to read.

---

