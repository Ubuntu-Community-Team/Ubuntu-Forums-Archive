---
title: "kernel update broke modules for Hauppauge 150"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by Episteme on 2006-09-19
The recent update seem to have messed up the ivtv drivers for my Hauppauge 150. 

Does this mean that I have to figure out the process all over again, or has someone else found a simple solution.

sean@pantheon:~$ cat /dev/video0 > /mnt/hdb1_storage/tv/tmp/temp.mpg
cat: /dev/video0: No such file or directory

grrr.

---

### Post by akolliop on 2006-09-19
Yeah, you just need to recompile, it's not too bad.
This site helps:
[http://www.abarbaccia.com/content/view/19/31/](http://www.abarbaccia.com/content/view/19/31/)

---

### Post by Episteme on 2006-09-20
Fair enough.

Thanks for the link.

---

