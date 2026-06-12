---
title: "Deleting stuff from root folder... possible to make files go to my trash can?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by inktri on 2008-01-03
My apache www folder is owned by root, therefore deleting files from the folder and then retrieving them (when necessary) becomes a major pain -- in fact I don't even know how to retrieve those files... is there a root trash can? How do I access it?

Is there a way to make deletion of root files also keep a copy in my own trash can?

---

### Post by forestpixie on 2008-01-03
you can open nautilus as root - gksudo nautilus 

I guess you could copy them to your trash

you can probably do all that with the cli - not sure how though

---

### Post by Vixis on 2008-01-03
root trash:
/root/.Trash/

you  can make alias or script like this:
#!/bin/bash
# delete to trash from terminal
mv "$@" home/username/.Trash/

---

### Post by inktri on 2008-01-03
thanks for the replies

where do i put that script so that all root files deleted will run that

---

### Post by Vixis on 2008-01-03
> **inktri said:**
> thanks for the replies

where do i put that script so that all root files deleted will run that

```
echo $PATH
```
will give you directories where you can add executables:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/home/victor/scripts

you can add:
```
PATH=$PATH:/scripts:/scripts/perl
export PATH
```

to /root/.bashrc

so you can put scripts also in /scripts or /scripts/perl

System-wide .bashrc file:
/etc/bash.bashrc

---

