---
title: "CDROM in Terminal"
date: 2010-03-11
forum: Apple Hardware Users
---

### Post by JeradJones on 2010-03-11
I can't access the CDROM in the terminal. I have tried /media or whatever it was and it didn't work. help?

---

### Post by linuxopjemac on 2010-03-11
are you on PPC ?

---

### Post by JeradJones on 2010-03-11
PPC? I'm using a Macbook Pro. I'm not sure what PPC is because I'm not a big computer person.

---

### Post by linuxopjemac on 2010-03-11
PowerPC, it's the architecture used in older Apple machines.

you might want to have a look where CDROM is mounted with
```
cat /etc/fstab
```

---

### Post by JeradJones on 2010-03-11
It says no such directory

---

### Post by linuxopjemac on 2010-03-11
?? I didn't know you have to be root to look at that, try:

```
sudo cat /etc/fstab
```

---

### Post by CharlesA on 2010-03-11
Could also verify that the cdrom is actually mounted by looking at what "mount" returns.

> **linuxopjemac said:**
> ?? I didn't know you have to be root to look at that, try:

```
sudo cat /etc/fstab
```

You don't need to be root to cat fstab, since the default permissions are 644.

---

### Post by JeradJones on 2010-03-11
nothings working. I just want to get to my cdrom in terminal

---

### Post by linuxopjemac on 2010-03-11
are you sure you put a space between cat and /etc/fstab ?

---

### Post by JeradJones on 2010-03-11
I did. I seriously don't understand why it won't work.

---

### Post by linuxopjemac on 2010-03-11
try to see if you have a fstab
```
cd /etc
ls -al | grep fstab
```

---

### Post by JeradJones on 2010-03-11
yup, i have it

---

### Post by CharlesA on 2010-03-11
Try using mount to see if the cdrom is already mounted, and if so where it is mounted.

```
mount
```

---

### Post by linuxopjemac on 2010-03-11
read it with
```
nano /etc/fstab
```
and see if you can figure out where cdrom is mounted automatically

---

### Post by JeradJones on 2010-03-11
How do I read where it's mounted

---

### Post by CharlesA on 2010-03-11
It is listed in your fstab file.

---

### Post by linuxopjemac on 2010-03-11
if you something like this:
```
/dev/cdrom      /mount/cdrom    udf,iso9660  noauto,owner,kudzu,ro   0 0
```
you know that the cdrom is mounted on /mount/cdrom

---

### Post by JeradJones on 2010-03-11
I can't find my fstab file

---

### Post by JeradJones on 2010-03-11
it says unknown file

---

### Post by linuxopjemac on 2010-03-11
copy and paste exactly what you are doing to the forum plus what ubuntu gives as output, cause what you tell us seems impossible

---

### Post by JeradJones on 2010-03-11
I can't copy and paste b/c it contains my full name
localhost:~ *****$ cat /etc/fstab
cat: /etc/fstab: No such file or directory
localhost:~ *******$ mount /dev/cdrom
mount: /dev/cdrom: unknown special file or file system.

---

### Post by linuxopjemac on 2010-03-11
are you in a live environment ?

---

### Post by JeradJones on 2010-03-11
idk

---

### Post by linuxopjemac on 2010-03-11
you are a real noob ;) I mean, did you boot from the Ubuntu CD or did you boot from the hard disk ?

---

### Post by JeradJones on 2010-03-11
im a serious noob b/c i dont know what boot means

---

### Post by linuxopjemac on 2010-03-11
hahahaha, you are funny. [http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)
booting a computer means starting it up. Did you install Ubuntu on your hard disk, or did you start your computer with an Ubuntu CD?

---

### Post by JeradJones on 2010-03-11
I believe hard disk because i havent used a c d on my computer till today

---

### Post by linuxopjemac on 2010-03-11
then I don't understand all your results, sorry....

---

### Post by JeradJones on 2010-03-11
no more suggestions?

---

### Post by linuxopjemac on 2010-03-11
maybe a silly question from my side, but are you sure you are working in Ubuntu Linux ?

---

### Post by CharlesA on 2010-03-11
Can probably find out for sure if they are running Ubuntu, by having the OP run this:

```
uname -a
```

---

### Post by linuxopjemac on 2010-03-11
If people don't even know whether they are running Ubuntu or not, they should not be posting here to my opinion.

---

### Post by CharlesA on 2010-03-11
Agreed.

---

