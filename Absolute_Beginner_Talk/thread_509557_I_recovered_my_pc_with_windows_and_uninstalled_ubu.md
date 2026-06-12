---
title: "I recovered my pc with windows and uninstalled ubuntu"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Pttyboy 92 on 2007-07-25
which now i realize i just lost half my hard drive:shock:, what do I do

---

### Post by shoaibi on 2007-07-25
There is a software called R-Studio, i think 3.3 is the latest relaese get that, or
get Undelete, or Get data back....
I use R-Studio....

---

### Post by dylan623 on 2007-07-25
> **Pttyboy 92 said:**
> which now i realize i just lost half my hard drive:shock:, what do I do

You can use GParted off of the LiveCD. Better yet, get rid of Windoze and only use Ubuntu.

---

### Post by Pttyboy 92 on 2007-07-25
> **shoaibi said:**
> There is a software called R-Studio, i think 3.3 is the latest relaese get that, or
get Undelete, or Get data back....
I use R-Studio....

It says its a demo

---

### Post by Pttyboy 92 on 2007-07-25
any links to a **free** peice of software to recover the partiotion, nothing i need to pay and i want to do it from windows

---

### Post by por100pre1 on 2007-07-25
Resize your Windows partition using Gparted included in the Ubuntu Live CD.

If you are using Vista you can use Disk Manager to increase your parttition, otherwise you'll need a3rd party program if you don't want to use the Ubuntu Live CD.

---

### Post by Pttyboy 92 on 2007-07-25
> **por100pre1 said:**
> Resize your Windows partition using Gparted included in the Ubuntu Live CD.
do u have to install ubuntu again, since that is what the disk does

---

### Post by Orochi on 2007-07-25
Are you trying to get back data you lost that was on your Ubuntu partition, or are you trying to resize your Windows partition to take up the whole drive? I'm unclear as to what the problem is.

---

### Post by por100pre1 on 2007-07-25
> **Pttyboy 92 said:**
> do u have to install ubuntu again, since that is what the disk does

No if you use the Ubuntu LiveCD... just don't click the installer.

---

### Post by Pttyboy 92 on 2007-07-25
> **Orochi said:**
> Are you trying to get back data you lost that was on your Ubuntu partition, or are you trying to resize your Windows partition to take up the whole drive? I'm unclear as to what the problem is.
resize the partition and make it just one hardrive

---

### Post by Pttyboy 92 on 2007-07-25
Let me ask, now im kind of changing subjects, but if I install ubuntu again, will it install in the "empty" or "Lost" partition?

---

### Post by Pttyboy 92 on 2007-07-25
bump

---

### Post by asmoore82 on 2007-07-25
> **Pttyboy 92 said:**
> Let me ask, now im kind of changing subjects, but if I install ubuntu again, will it install in the "empty" or "Lost" partition?

yes if you tell it to

---

### Post by Pttyboy 92 on 2007-07-25
> **asmoore82 said:**
> yes if you tell it to
how?

---

### Post by hessiess on 2007-07-25
just use the use free space option.

 its a bad idea to only have one huge partition with everything, your files can become mixed up with os files, it can become verry hard to orgonise, if you have a bad filesystem error, you may loose the whole partition. although it is verry unlickly

have somthing like:

extended partition
____documents
____midia
____misc

---

### Post by Orochi on 2007-07-26
> **Pttyboy 92 said:**
> how?

When you install Ubuntu just tell it to use all available free space.

If you want to resize Windows to gain space back, you can use gparted from the live cd to resize your NTFS partition. However NTFS resizes can sometimes be dangerous, and Windows sometimes will be unable to boot without a reinstallation. Therfore you should backup all your data before resizing. Alternately, you could just create a new NTFS partition in the free space for Windows to use instead of resizing your current ones (Windows will see it as a second drive).

---

### Post by sdowney717 on 2007-07-26
very easy simply boot the ubuntu live cd
then click install follow the prompts then
when it get to partitioning part choose manual

Then it will show a resizer. Make the ntfs partition as big as you can apply it and then
cancel the install
 simply reboot the machine

And it is done.

Windows will complain and do a disk check

So why did you not like ubuntu?

---

### Post by sdowney717 on 2007-07-26
before you shrink an NTFS partition it should be defragged. I suppose because the files in windows can be scattered alll over the drive in your free space at the end of the partition. So when you make it smaller, I suppose those windows files get truncated, pretty sloppy.

With ext3 partitions you dont have to defrag the drives.

---

### Post by hessiess on 2007-07-26
> With ext3 partitions you dont have to defrag the drives.

so long as you ceep 20% of the drive as free space

---

### Post by Espreon on 2007-07-27
Why are you descending back into Windows hell?

---

