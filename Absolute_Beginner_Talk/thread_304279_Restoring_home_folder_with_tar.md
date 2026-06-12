---
title: "Restoring home folder with tar"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-11-21
Hi

The path for my home folder is /home/roger. I've used the archive feature in Nautilus to create a tar file of my home folder on an external hard disk - path: /media/"My Book"/roger.tar. What I want to be able to do is to re-create my home folder in the event of a hard disk failure. Assuming I get a new PC/hard disk, and I re-install Ubuntu, what command would extract roger.tar from the external hard disk and install all the files into the new /home/roger folder?

Regards

Roger D

---

### Post by mark_g on 2006-11-21
Try

tar -xvf /media/"My Book"/roger.tar -C /home/roger

(x: extract v: be verbose f: filename C: change directory to)

you should can test it by extracting it to another directory e.g.

mkdir /home/testdir
tar -xvf /media/"My Book"/roger.tar -C /home/testdir

---

### Post by taurus on 2006-11-21
> **mark_g said:**
> 
mkdir /home/testdir
tar -xvf /media/"My Book"/roger.tar -C /home/roger
Shouldn't that be

```
tar -xvf /media/"My Book"/roger.tar -C /home/testdir
```

---

### Post by mark_g on 2006-11-22
Taurus is right. It should be:

```
mkdir /home/testdir
tar -xvf /media/"My Book"/roger.tar -C /home/testdir
```

I was almost falling asleep as I was typing it, so I hope you didn't overwrite your curren home directory while testing it... :-?

---

### Post by RogerD on 2006-11-23
> **mark_g said:**
> Taurus is right. It should be:

```
mkdir /home/testdir
tar -xvf /media/"My Book"/roger.tar -C /home/testdir
```

I was almost falling asleep as I was typing it, so I hope you didn't overwrite your curren home directory while testing it... :-?

Thanks for the advice. It all sounds straightforward, and I've created testdir using sudo. My only concern is that this isn't quite the situation I'll face if I'm trying to re-build my home folder on a new PC. testdir is a completely empty folder, when I re-install Ubuntu, I'll be creating a roger folder as the prime user of the system, so this folder won't be empty. Will this make any difference?

---

