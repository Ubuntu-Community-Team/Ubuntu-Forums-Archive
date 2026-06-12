---
title: "Change name of partition?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-04-25
Is there a way I can change the names of my partitions, so they are called something more descriptive than 'disk' and 'disk-1'?

Thanks.

---

### Post by aberry5555 on 2007-04-25
no you can't, as these are not really "names", they are actual physical markers. The one thing you can do is mount the hard-drive in folder with the name of your choice e.g.

```
sudo mount /dev/hda1 /media/Movies
```

---

### Post by trishacupra on 2007-04-25
Would that be a permanent thing, or would I have to keep mounting the hard drives in those folders each time I boot up?

---

### Post by nixclusive on 2007-04-25
You can make the mount points permanent by editing  the file: /etc/fstab 
This is what the systems reads to determine which filesystems are to be mounted and where. 
Take a look at the file itself, open the terminal and enter: ```
less /etc/fstab
```
If you are not comfortable with editing this thing, come back and look for the keyword /etc/fstab in the forums.

---

### Post by nixclusive on 2007-04-25
Ok hey check this out: 
[http://rute.2038bug.com/node22.html.gz#SECTION002270000000000000000](http://rute.2038bug.com/node22.html.gz#SECTION002270000000000000000)

A very nice explaination of the file system table: /etc/fstab

---

### Post by trishacupra on 2007-04-25
Thanks so much for pointing me in the right direction. Knowing what to look for, I found this: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html).

I found it to be a user-friendly, simple explanation for a newbie like me. 

Looks easy. :)

---

