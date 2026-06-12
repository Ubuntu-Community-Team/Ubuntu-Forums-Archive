---
title: "um, help, please"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by jesus of suburbia on 2006-08-15
I am building a new pc but how can i format a brand new hard drive with linux? ive worked out the partition stuff

---

### Post by JerMe on 2006-08-15
I'm assuming you're in Ubuntu now...

Applications > Accessories > Terminal

type these commands:
```
sudo apt-get update
```
```
sudo apt-get install gparted
```

That'll install GParted, which will allow you to format your brand new hard drive with Linux, just like you did when you installed Ubuntu.

---

### Post by jesus of suburbia on 2006-08-15
thanks very much!!!!

---

### Post by Titus A Duxass on 2006-08-15
If it is a brand new empty hard drive just run the installation procedure, partitioning is part of that (surprisingly enough).

---

