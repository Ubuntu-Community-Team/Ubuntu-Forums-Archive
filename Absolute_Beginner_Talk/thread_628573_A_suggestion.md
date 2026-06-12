---
title: "A suggestion"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by simons-photography on 2007-12-01
I have a little problem with installing ubuntu, ok I normally create a new partition in the instalation but I have a problem I can hardly tell one partition from another and a couple are similar sizes infact I just wipped out a raid0 partition by mistake (not thinking ubuntu would support intel matrix raid and it did rec havoc but that another story and another thread) luckily it was only a scratch parttion I don't remember having anything important on it.

now why can't the volume labels come up when we go to partiotion for the instalation ? I know there is a specific way linux shows drives but as I have 8 parttions and 6 ports on my computer is all and 4 HDDs that gets way confusing. every parttion has a label under windows so can't these labels come up in the instalation saving errors ? could it be in the next version please ? just a though I am now reformating back to original setup and will investigate the "intel matrix raid" + Ubuntu scenario before proceding I don't really want to loose 150 GB of photography...

---

### Post by jken146 on 2007-12-01
The linux way of labelling partitions is, in my opinion, very intuitive.  If you look at your disks in gparted you will see the labels that you have given to the partitions (gparted is on the live CD).  If you have trouble remembering which is which maybe you should draw yourself a diagram.

I do agree though, that the labels should appear in the installer partitioner.  I preferred it when it was just gparted's gui in the installer (Edgy or Fiesty I think).

---

### Post by simons-photography on 2007-12-01
the default partition utility in the setup prcedure does not by default show any labels and considering I have 10 SATA ports on my mobo an IDE port and a raid that may or may not show up its a bit hard to predict what will be where on the list

---

### Post by jken146 on 2007-12-01
I disagree that it's hard to predict what will be where.  The first SATA drive will be sda, the second sdb, the nsdc, sdd, and so on.  The partitions on sda will be sda1, sda2, sda3, etc.  These partition names appear in the column named 'Device'.

---

### Post by simons-photography on 2007-12-01
yea I'd have to consult my mobo manual and open the pc to remember which of the 4 HDD is plugged in where with 2 sata controllers and a IDE channel how am I to know what has priority in the manual there is port 0-7 of intel matrix raid and gigabyte controller with ports 0 and 1 it don't tell me who comes first and if my raid will be recocnised and if it will properly by ubuntu

---

### Post by jken146 on 2007-12-01
Yes, that does sound a little tricky.  They really should include the user-given labels in the installer.  However, until they do that, you can go in gparted on the live CD prior to install and the labels are listed there along with the linux /dev/sda2 type names.

---

