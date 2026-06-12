---
title: "primary/logic partition"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by yeheii on 2007-06-26
Hello.

I installed Feisty 64bit using alternate CD.
i would like to partition like this:

C: 40 Gb [windows xp] ntfs
D: 50 Gb raw
E: 14 Gb /root
F: 12 Gb /home
G: 1 Gb /swap

I can't partition drives F and G 'cause it will display   "UNUSABLE".  Why is that so?

And I tried auto partitioning but there's no /home
and the /swap is in betweenm like:

D: 50 Gb
E: 1 Gb   /swap
F: 26 Gb /root

help

---

### Post by yeheii on 2007-06-26
up

---

### Post by derby007 on 2007-06-26
Just checking if you are using the correct filesystems for each partition: ie. ext3 for / (& not /root), ext3 for /home, swap for /swap, and maybe fat32 for your 50G as Win & Linux both R/W to FAT32.

---

### Post by yeheii on 2007-06-26
yup, they are assigned like that.  but i can't change the / to primary.
when i partition it, it automatically assign itself as Logic

---

### Post by Inxsible on 2007-06-26
You can have at max 4 primary partitions. Do you have other partitions there?
 
Is there a reason you want / to be primary ? Ubuntu runs off of an extended partition just fine. Mine is set up as an extended as well.

---

### Post by yeheii on 2007-06-26
before i installed ubuntu, i have 40 Gb with Win xp installed and 50 Gb raw but partitioned.
and the rest free space. (for 120Gb HD)
 i'm not sure if there's a problem with the / , /home, and swap as all logic because after installation, i restart my pc, it just blacks out, hang.

---

### Post by Inxsible on 2007-06-26
> **yeheii said:**
> before i installed ubuntu, i have 40 Gb with Win xp installed and 50 Gb raw but partitioned.
and the rest free space. (for 120Gb HD)
i'm not sure if there's a problem with the / , /home, and swap as all logic because after installation, i restart my pc, it just blacks out, hang.
 
That could probably be because of other issues, like your graphics processor. Not due to the fact that your / is on an extended partition.

---

### Post by bodhi.zazen on 2007-06-26
> **yeheii said:**
> Hello.

I installed Feisty 64bit using alternate CD.
i would like to partition like this:

C: 40 Gb [windows xp] ntfs
D: 50 Gb raw
E: 14 Gb /root
F: 12 Gb /home
G: 1 Gb /swap

I can't partition drives F and G 'cause it will display   "UNUSABLE".  Why is that so?

And I tried auto partitioning but there's no /home
and the /swap is in betweenm like:

D: 50 Gb
E: 1 Gb   /swap
F: 26 Gb /root

help

Partitioning in Linux is different the partitioning in Widows, at least in terminology [ie linux uses /dev/hdxy rather then C:\ D:\ ... ]

The short answer is you can only have 4 primary partitions.

You can convert a primary partition to an extended partition which may then contain additional logical partitions.

Confused yet ?

Take a look at this : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by yeheii on 2007-06-26
@Inxsible

I use an ati radeon x550 pci-ex card

@bodhi

i see.  how do you set each partition as primary or logical?
'cause when i partition something as /root, /home automatically selects primary also
without asking me to choose logical or primary.
or is it okay if all the ubuntu partitions are logical?

---

### Post by Inxsible on 2007-06-26
> **yeheii said:**
> @Inxsible
 
I use an ati radeon x550 pci-ex card
 
@bodhi
 
i see. how do you set each partition as primary or logical?
'cause when i partition something as /root, /home automatically selects primary also
without asking me to choose logical or primary.
or is it okay if all the ubuntu partitions are logical?
 
Yes, all logical for Ubuntu is perfectly fine. My setup is exactly the same. My root /home and swap are all logical partitions.

---

### Post by bodhi.zazen on 2007-06-26
I usually do my partitioning before I install.

Run gparted from the desktop CD. You can then select primary or extended/logical.

Then run the installer and set your mount points as it were. During the install the partitions can/will be formatted.

Gparted "2 Page review" [http://techgage.com/article/gparted_livecd_31-1/1](http://techgage.com/article/gparted_livecd_31-1/1)

---

### Post by yeheii on 2007-06-26
@Inxsible

okay, will try installing it again tomorrow.  thanks!

@bodhi

thanks for the link on paritioning!

---

