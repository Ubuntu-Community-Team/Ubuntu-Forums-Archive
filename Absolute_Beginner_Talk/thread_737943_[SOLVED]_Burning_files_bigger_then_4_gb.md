---
title: "[SOLVED] Burning files bigger then 4 gb"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by thomas7.10 on 2008-03-28
Hi!

It seems to be a generel problem in ubuntu for serveral years that there isn't the possiblity to burn files bigger then 4gb. People write about something alled backports what should help to update something and get it to work that way.

Me i tried just isntalling gnome baker and k3b.

So could someone please help me throw this?

Thomas

---

### Post by logos34 on 2008-03-28
you mean the udf extension which is enabled by K3b and other apps for files bigger than 2 gb won't work for over 4 gb?

---

### Post by insane_alien on 2008-03-28
i can't say i've ever encountered this before. infact i just burned a 7GB image onto a dual layer DVD.

i used brasero and gutsy. it also works on hardy.

---

### Post by jayde6 on 2008-03-28
You can burn it after turning it into a disc image with a command like this

```
genisoimage -udf -allow-limited-size -r -J -V "Disc Name" -o ~/image.iso /path/to/bigfile
```

I found it here;
[http://ubuntuforums.org/showthread.php?t=623322](http://ubuntuforums.org/showthread.php?t=623322)
with thanks to tkmn.

I believe the latest version of brasero (which i belive is included with hardy) has this fixed.

---

### Post by thomas7.10 on 2008-03-28
Thank you it worked

---

