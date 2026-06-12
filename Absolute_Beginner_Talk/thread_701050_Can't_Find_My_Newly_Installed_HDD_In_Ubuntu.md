---
title: "Can't Find My Newly Installed HDD In Ubuntu"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by wilson.jacob8 on 2008-02-18
I just installed another hard drive to a computer running ubuntu 7.10 gutsy gibbon to increase my overall storage, but it is nowhere to be found. the only place that i can see it in is my partition manager but other than that i can't find or mount it. 


there is probably some simple answer that i am just over looking, any ideas or help on finding my hard drive would be greatly appreciated.

thanks

---

### Post by sisco311 on 2008-02-18
please post the output from:

```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by hyper_ch on 2008-02-19
where do you want to have that disk mounted to?

---

### Post by talsemgeest on 2008-02-19
Have you checked in your /media folder? I know its kind of obvious but everyone makes mistakes :)

---

### Post by jan quark on 2008-02-19
you can also check here if the drive is mounted or not

go to places > computer > filesystem > media or mnt

do you see it there, if not it must be mounted manually and added to the fstab file

---

### Post by wilson.jacob8 on 2008-02-19
i will try this stuff when i get home to my ubuntu computer tonight.


thanks for the help so far

---

