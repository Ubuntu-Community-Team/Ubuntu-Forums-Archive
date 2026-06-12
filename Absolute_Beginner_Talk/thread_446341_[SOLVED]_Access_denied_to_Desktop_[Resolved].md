---
title: "[SOLVED] Access denied to Desktop [Resolved]"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by therandman on 2007-05-16
Have no clue what I did (maybe having something to do with trying to get Adobe Reader installed on Kubuntu Feisty 64), but now I can't delete/add anything on the desktop.  Not too many threads about this; any one have a direction to point me in?  I've used most of my brain cells for the Adobe problem (I need it to use fillabe pdf's.)

And yes, I LOVE Kubuntu!

---

### Post by wormser on 2007-05-16
It sounds like your permissions are messed up on the desktop.  Post the results of Desktop line.

```
cd
ls -l 
```

---

### Post by therandman on 2007-05-16
```
total 8756
drwxr-xr-x  4 root    root       4096 2007-05-15 23:02 Desktop

```

---

### Post by aysiu on 2007-05-16
Yup. Your desktop's owned by root. Paste this command in: ```
sudo chown -R randman:randman /home/randman/Desktop
```

---

### Post by therandman on 2007-05-16
Thanks aysiu, worked perfectly!! :)

Have to file that into the "Need to absolutely remember upon penalty of death" directory

---

### Post by aysiu on 2007-05-16
P.S. This may help explain how the ownership changed in the first place:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Hobo Joe on 2007-05-16
> **therandman said:**
> Thanks aysiu, worked perfectly!! :)

Have to file that into the "Need to absolutely remember upon penalty of death" directory

Man, I don't know what I would do without one of those! :D

---

### Post by varonbondumb on 2008-05-20
> **aysiu said:**
> Yup. Your desktop's owned by root. Paste this command in: ```
sudo chown -R randman:randman /home/randman/Desktop
```

my problem was similar:
i activated a partition on my hard disk and was not allowed permission to do anything on it.  after finding this code and typing it (changing "randman" to the proper thing and the "/home/randmna/Desktop" to where the disk was), everything worked properly. 

thank you very much

---

