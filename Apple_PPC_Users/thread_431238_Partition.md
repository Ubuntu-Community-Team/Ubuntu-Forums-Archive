---
title: "Partition"
date: 2007-05-02
forum: Apple PPC Users
---

### Post by royjg2 on 2007-05-02
Using Kubuntu on ppc G5
Had created partitions before installing linux
It mounted itself on smallest partition which is almost full
Other  23 gegs partition is formated as ext 3 but i am not able to make it active using any of the partition programs
Any suggestion to make it active for linux to make use of it ?
Thank you
:KS

---

### Post by Gen2ly on 2007-05-02
> **royjg2 said:**
> Using Kubuntu on ppc G5
Had created partitions before installing linux
It mounted itself on smallest partition which is almost full
Other  23 gegs partition is formated as ext 3 but i am not able to make it active using any of the partition programs
Any suggestion to make it active for linux to make use of it ?
Thank you
:KS

If I understand correctly.  You can move your home folder to the new partition by editing fstab.  Is this what u r asking?

---

### Post by royjg2 on 2007-05-03
Actually Yes :)

---

### Post by royjg2 on 2007-05-07
I know i have fstab installed
But I do not know how to edit it to move home folder to that partition :( 
Thanks

---

### Post by DJ_Max on 2007-05-08
/etc/fstab is just a plain text file. You have to edit it with root privileges, than you have to reconfigure Yaboot.

Do a 
```
cat /etc/fstab
```

and

```
cat /etc/yaboot.conf
```

Also see the names of your partitions, (if you don't already know)

Assuming your HD is /dev/hda
```
fdisk /dev/hda
```

Than enter the command ```
p
```

---

