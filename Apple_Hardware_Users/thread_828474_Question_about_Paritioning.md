---
title: "Question about Paritioning"
date: 2008-06-13
forum: Apple Hardware Users
---

### Post by WillJeffery on 2008-06-13
Ok so here we go:
In the MacBook Santa Rosa set-up wiki it says: 

```
#

Install ubuntu as usual, except:

    *

      In the partitioner, select Manually edit partition table
    *

      Delete /dev/sda3 and /dev/sda4 if they exist
    *

      Create a new ext3 partition for your root
    *

      Mount the newly created ext3 partition on '/'
    *

      Note that Boot Camp will cause problems if you make more than two partitions in total.


```

However, I am trying to dual boot OS X and Ubuntu, so how do I partition/format correctly without destroying my OS X boot?

This is my planned paritioning:
149 GB Total
130 GB to OS X (HFS+)
17GB to Ubuntu (ext3 on '/')
2GB to Linux swap (swap)

Can I follow those exact instruction and be safe? Or I only delete /dev/sda3 and /dev/sda4 if they exist on the 17GB Ubuntu parition?

tyvm in advance!

---

### Post by cyberdork33 on 2008-06-13
> **WillJeffery said:**
> However, I am trying to dual boot OS X and Ubuntu, so how do I partition/format correctly without destroying my OS X boot?
You seemed to have missed step 4:
> If necessary, use Boot Camp to resize your OSX partition and make space for Ubuntu. Don't waste a CD creating a Windows driver disk. Reboot.

If you do not have bootcamp available, you can still use the [OSX terminal commands]("http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes"), or use gparted  on the Ubuntu LiveCD.

Once you get the OSX partition down to size, boot the Ubuntu Live CD, start gparted and delete any partitions after your HFS+ partition. Then start the Ubuntu installer and choose to install to the free space. If you know what you are doing, you can use the manual partitioner in the installer to create your root and swap manually.

---

### Post by Zaff on 2008-06-16
Just following up, I'm reinstalling ubuntu (Hardy this time, I installed Gutsy previously) and I don't remember seeing this :
> 
Note that Boot Camp will cause problems if you make more than two partitions in total.

What does that mean exactly ? what should be expected ? I don't like having everything on the same partition so I would like to have a / and a /home separated. I'm using rEFIt to boot.

---

### Post by cyberdork33 on 2008-06-16
> **Zaff said:**
> What does that mean exactly ? what should be expected ? I don't like having everything on the same partition so I would like to have a / and a /home separated. I'm using rEFIt to boot.Bootcamp assistant will not run with more than one partition on the disk. No matter, you have other tools at your disposal.

---

