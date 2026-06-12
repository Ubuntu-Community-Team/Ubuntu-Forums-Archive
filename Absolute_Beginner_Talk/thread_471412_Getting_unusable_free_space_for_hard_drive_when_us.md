---
title: "Getting unusable free space for hard drive when using text installer Ubuntu 6.06"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by salalejo on 2007-06-12
I'm trying to partition my hard drive for the Ubuntu 6.06 installation.  I can't use a live CD for whatever reason so I'm using the text installer.  I'm able to do everything until the partitioning.  I am manually editing the partitions.  So first I make the "\" partition and make sure its bootable with size 5 GB.  Then I made a swap partition of 1 GB.  So between these two partitions I'm left w/ 5.2 GB of free space which the ubuntu installer says is "Unusable".  However, I want to make this "\home".  What am I doing wrong?

---

### Post by Bachstelze on 2007-06-12
Are the root and swap the only partitions you have ?

---

### Post by salalejo on 2007-06-12
Yes, those are the only ones I can make.  I tried making the root, then home partition, then making the swap.  But then the space I allocated to the swap also becomes unusable.  Whatever space I leave as third becomes unusable no matter what order I go in.  I partitioned the drive with a utility on rescuedisk cd.

---

### Post by salalejo on 2007-06-12
help someone pretty please?

---

### Post by Inxsible on 2007-06-12
> **salalejo said:**
> help someone pretty please?

Are you making them to be primary partitions ? Do you already have 2 Windows/other partitons on the drive ?

You cannot have more than 4 primary partitions on a drive. Try to make an extended partition and place /, /home and swap as logical partitions inside the extended partition.

---

### Post by salalejo on 2007-06-12
Oh, yes, I already have another 2 Windows partitions on the Hard Drive :-)  I will do that, one sec...

---

### Post by Bachstelze on 2007-06-12
> **salalejo said:**
> Oh, yes, I already have another 2 Windows partitions on the Hard Drive :-)

That was what I meant when I asked if root and swap were your only partitions ;)

---

### Post by salalejo on 2007-06-12
is the following picture the correct set up?

[http://img.photobucket.com/albums/v323/salalejo/IMG_1633.jpg](http://img.photobucket.com/albums/v323/salalejo/IMG_1633.jpg)

---

### Post by Inxsible on 2007-06-12
I would give /home a lot more space if I were you.

I have 
/ = 9 GB
/home = 20 GB
swap = 1GB

---

### Post by salalejo on 2007-06-12
I have 16.2 GB of free space.  Should I make it bigger and grab a bigger chunk of the XP install?  I'm barely starting Ubuntu so I'm not sure how much I'll actually use it come a month from now...

---

### Post by Inxsible on 2007-06-12
Ever since I installed Ubuntu, I have not logged into my Windows except to verify that i didnt break anything in Windows.

You will get hooked on Ubuntu too. If you can spare space from the XP install, then i would suggest you do that. Also depends on which OS you plan to make your default.

For me, I have gone totally Linux...so my answer would be biased. I have windows only for a couple of games that I really like and Turbo Tax. All of everything that i do, i have found alternatives in Linux.

---

