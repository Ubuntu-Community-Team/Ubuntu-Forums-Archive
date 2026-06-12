---
title: "uninstall ubuntu???"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by gazz1982 on 2008-03-23
I've wipped windows xp from my old machine and installed ubuntu now i need to uninstall ubuntu temporarily and re- install it 

How do I completly wipe it and format the hard drives ready for me to install it afresh ?

---

### Post by saj0577 on 2008-03-23
Just start installing it and during the install process delete all partitions (live cd)

Saj

---

### Post by overdrank on 2008-03-23
> **gazz1982 said:**
> I've wipped windows xp from my old machine and installed ubuntu now i need to uninstall ubuntu temporarily and re- install it 

How do I completly wipe it and format the hard drives ready for me to install it afresh ?

Hi and this may help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by ugm6hr on 2008-03-23
This ([http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)) has links to Hard Disk wiping tools.

The Ubuntu LiveCD has GParted (Partition Editor), which allows you to reformat drives and delete partitions too.

---

### Post by gazz1982 on 2008-03-24
I put the cd in and then started the machine

various options came up

so I chose* start or install*

this just booted using it as a live cd

is there any code i can use to wipe the hard drives?

---

### Post by Barrucadu on 2008-03-24
You could delete or reformat the partition through gparted. That would remove everything. Or, you could use the *forbidden method* which is warned against in many places.

```
sudo rm -rf /
```

That will delete everything on your harddrive (and any mounted drives/partitions), in every folder, without asking for confirmation. Use at your own risk.

---

### Post by ugm6hr on 2008-03-24
> **gazz1982 said:**
> is there any code i can use to wipe the hard drives?

Yes - Partition Editor in System Menu.

---

### Post by dptxp on 2008-03-24
you can delete,create resize and format partitions in step 5 while installing ubuntu after clicking on 'install'.
Just select 'manual' in step 4.

---

