---
title: "What partitions are created?"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by _Mike_ on 2006-10-10
What partitions are created during the install process when allowing the partitioning tool to automaticly create the partitions?

What mount points are these partitions using?

I'm having a heck of a time trying to install Ver 6.06 (Dapper)on my system. Either it fails to boot to the hard drive after installation or GRUB fails to install during the process. I've tried both the automatic and manual partitioning. I've reburned the image to CD at a much lower speed to, hopefully, eliminate any errors. Both CDs passed the Ubuntu CD test. 

Thanks for the help.

---

### Post by haggo on 2006-10-10
i need help with this to, anyone know ??

---

### Post by gn2 on 2006-10-10
> **_Mike_ said:**
> What partitions are created during the install process when allowing the partitioning tool to automaticly create the partitions?

What mount points are these partitions using?

I'm having a heck of a time trying to install Ver 6.06 (Dapper)on my system. Either it fails to boot to the hard drive after installation or GRUB fails to install during the process. I've tried both the automatic and manual partitioning. I've reburned the image to CD at a much lower speed to, hopefully, eliminate any errors. Both CDs passed the Ubuntu CD test. 

Thanks for the help.

Have you got enough RAM? Need 256 for install from live disc.

---

### Post by _Mike_ on 2006-10-10
I've got 384MB of RAM.

---

### Post by noobie2 on 2006-10-10
I installed Dapper over the weekend.  During the set up I used the partition manager to create the following partitions:
/        (the root area)
/swap    (the swap file area)
/home    (an area for everything else)

I remember one of the settings for the /root partition was to mark it as a boot partition.  Did you set this flag?

---

### Post by bulldog on 2006-10-10
Should be enough.

If you let gparted decide for you,it makes a /   [root] partition and a swap.

If GRUB is not installed you can do it from the live cd,

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by _Mike_ on 2006-10-10
I had the root partition flagged as bootable.

---

### Post by _Mike_ on 2006-10-10
noobie2,

Do I mount /boot in the root partition?

---

### Post by _Mike_ on 2006-10-11
Thanks to all for the help. I set up partitions as noobie2 suggested and it installed and finally booted from the hard drive. 

I know it's an old, slow system but I never thought it would take 5 minutes to boot to the desktop. I've got some other issues to resolve, just have to do some research on the forum to find the answers.

Again, THANKS to all.

---

