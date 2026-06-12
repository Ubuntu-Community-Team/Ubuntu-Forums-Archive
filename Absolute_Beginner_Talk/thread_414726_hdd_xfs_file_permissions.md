---
title: "hdd xfs file permissions"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by thomas.hoyland on 2007-04-20
hi all

my new 500gb iomega usb hdd arrived and i want to format it was xfs and i can do exactly that (i used gparted)

however when i plug it in i have no permssion to write to it. i can read but not write (defeats the objective of a hard drive i think, lol)

anyway, as im no wizz with ubuntu
how do i change the permissions so i can write to it??

please help, as im considering a fat32 partition (shock horror)

regards,
Tom

---

### Post by Famicommie on 2007-04-20
Open up a terminal and type
```
sudo chmod 777 -R /path/to/hdd
```
Replace /path/to/hdd with whatever the path is.

To learn more about using chmod to change permissions, open up a terminal and type ```
info chmod
```

---

### Post by thomas.hoyland on 2007-04-20
> **Famicommie said:**
> Open up a terminal and type
```
sudo chmod 777 -R /path/to/hdd
```
Replace /path/to/hdd with whatever the path is.

To learn more about using chmod to change permissions, open up a terminal and type ```
info chmod
```

im afraid thats not working at all
im still unable to write to the drive

---

### Post by stimpack on 2007-08-22
Did you manage to sort this problem out?. 

I have this same problem with an XFS formatted USB drive. I do not have this problem with similar Reiser or ext3 drives, but I wanted to try xfs doh.

---

### Post by rockstar on 2008-01-19
This worked just fine for me.  I found this thread extremly confusing but somewhat helpful:

[http://ubuntuforums.org/showthread.php?t=283131&highlight=set+permissions+xfs](http://ubuntuforums.org/showthread.php?t=283131&highlight=set+permissions+xfs)

---

