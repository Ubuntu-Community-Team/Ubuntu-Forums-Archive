---
title: "console commands"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by verbatim210 on 2006-06-26
mv htdocs /var/www/ - will move htdocs into /var/www/htdocs
how do i move all the contents inside htdocs into /var/www?

thanks
verbatim

---

### Post by scxtt on 2006-06-26
mv htdocs/* /var/www

---

### Post by verbatim210 on 2006-06-26
thx scxtt, works like a charm.  can i ask, does this function overite, update or...?

---

### Post by IYY on 2006-06-26
Depending on the arguments you give it, it can do anything you like. Read the manual page to see how to do it:

man mv

---

### Post by verbatim210 on 2006-06-26
thank you IYY, you taught me something new :)

---

### Post by DCM36 on 2006-06-26
This isn't totally relevent to this thread, but [here]("http://www.pixelbeat.org/cmdline.html") is a good page with command line tips.

---

### Post by verbatim210 on 2006-06-26
a paradise of commands, thanks for that DCM36!

     ...this will keep me occupied for another  day or two

---

### Post by verbatim210 on 2006-06-27
what is the linux equivalent of...
MS-DOS c:\format d:

---

### Post by 23meg on 2006-06-27
[QUOTE=verbatim210]what is the linux equivalent of...
MS-DOS c:\format d:[/QUOTE]
See the manpage for "mkfs".

Something else you'll like: [http://linuxcommand.org](http://linuxcommand.org)

---

### Post by Brunellus on 2006-06-27
[QUOTE=verbatim210]what is the linux equivalent of...
MS-DOS c:\format d:[/QUOTE]
note that you cannot format, resize, fsck (check the man page) or otherwise touch partitions when they are mounted.  you can only do that when they are unmounted.

---

### Post by verbatim210 on 2006-06-27
so how do u unmount, 
wipe out the partitioin, 
then mount it back on?
im just trying to do all the stuff the linux partitioner 
does in the install screen without 
needing to actually installing the os.

---

### Post by verbatim210 on 2006-07-02
what is the command to set/share a folder?

example:
/media/hdb1 is a totally empty clean HD and i want to share it for ftp access.
the ftp client can read everything, can write to the /home/ directory but **cannot **write to the hdb1 directory

thank you
verbatim

---

