---
title: "[SOLVED] un-do mkdir!"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by mandrill on 2007-10-26
I did this :  sudo mkdir /home/jim/disk

and want to un-do it. cannot quite figure it out - please help!

---

### Post by RomeReactor on 2007-10-26
Hi. Try:
```
sudo rm -r /home/jim/disk
```

---

### Post by thelocust on 2007-10-26
```
 
sudo rmdir /home/jim/disk

``` I think if not try
```
 
sudo rmdir -r /home/jim/disk

```

---

### Post by Maestro23 on 2007-10-26
Edit: Too Slow.

---

### Post by dfreer on 2007-10-26
I always find it easiest to delete a directory like so:
```
rm -Rv */home/jim/disk*
```
You don't need to worry about whether the directory is empty/full, it just deletes the stupid thing :D

---

### Post by mandrill on 2007-10-26
> **thelocust said:**
> ```
 
sudo rmdir /home/jim/disk

``` I think if not try
```
 
sudo rmdir -r /home/jim/disk

```


sudo rmdir /home/jim/dis was the one....I had it surrounded, though! 

Thanks everybody! been up too long.....

---

### Post by mandrill on 2007-10-26
> **dfreer said:**
> I always find it easiest to delete a directory like so:
```
rm -Rv */home/jim/disk*
```
You don't need to worry about whether the directory is empty/full, it just deletes the stupid thing :D
 This worked as well, tried it again, since the point is to learn something - thanx, people!

---

