---
title: "Permission to delete locked file"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-15
Hi, I'm trying to delete a document from my external drive, but the folder has a locker on it and it says that I don't have permission. what can I do to delete it? It's a folder full of music and videos that I already have in another folder, so I have them in double, and it's taking place for nothing.

Thanks!

---

### Post by taurus on 2007-03-15
What format is that external harddrive?  If it's ntfs, then you can delete it unless you have installed ntfs-3g driver first.

Otherwise, try to delete it with either sudo or with nautilus.  Just browse to where you want to delete it.

Applications - > Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by julie_lebou on 2007-03-15
I really need more details... how do I know what format is my drive and also, you said sudo or nautillus, but you put both of them in the code box... and also, I don't know what to write after the code, really new to Linux Thanks!

---

### Post by taurus on 2007-03-15
Open a terminal, Applications -> Acessories -> Terminal, and paste the output of this command here.

```
sudo fdisk -l
```
Now, which partition holds those duplicated movies and music?  

This code

```
gksudo nautilus
```
means you run nautilus as root, or super user if you want to view it that way, so you can delete stuff as root since you can't delete stuff outside your $HOME directory.

---

### Post by Madmoose on 2007-03-25
> **taurus said:**
> What format is that external harddrive?  If it's ntfs, then you can delete it unless you have installed ntfs-3g driver first.

Otherwise, try to delete it with either sudo or with nautilus.  Just browse to where you want to delete it.

Applications - > Accessories -> Terminal
```
gksudo nautilus
```


Mwahahaha! I've had a folder that has been bugging me forever, and now... It's gone! 

Thanks

---

### Post by zvacet on 2007-03-26
If you don´t want write** gksudo nautilus** every time look here
[http://doc.gwos.org/index.php/Nautilus_Scripts]("http://doc.gwos.org/index.php/Nautilus_Scripts")

---

