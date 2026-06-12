---
title: "Ubuntu install hang at partition"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by branduntu on 2006-12-31
](*,) I have a Dell Inspiron 8100 with a 30 GB drive.  I have defreged the drive to create 13 GB to dual boot Edgy.  Test of install disk (not alt) shows it is ok.

The first 4 steps of install go great...at step 5 & 6 partitioning will hang.  All I get is a spinning wheel.

On my other laptop, it works just fine with the same disk.

Is this a hard drive thing with the Dell?  Any suggestions?](*,) 

PS.  This community help forum is great...I like it!!!

---

### Post by Bartender on 2006-12-31
I think your situation was discussed over here

[http://www.ubuntuforums.org/showthread.php?t=327923](http://www.ubuntuforums.org/showthread.php?t=327923)

---

### Post by branduntu on 2006-12-31
You rock!!!  I saw this link once and could not find it again.  thank you!!!:D

---

### Post by Bartender on 2006-12-31
Glad to help.  As soon as I saw yours I knew I'd read something similar just five minutes earlier.  Fortunately that was within my short-term memory loss window :)

---

### Post by Ergo on 2006-12-31
I had a similar problem due to XP's hidden agenda:evil: .  In my case I intended on using the entire partition anyway.  In this case use Ubuntu to delete the partition, then "create new", and it will work fine afterward.  Ubuntu formats it into oblivion:mrgreen: .

---

### Post by branduntu on 2006-12-31
](*,) Hey Guys,

I have been through these steps numerous times and nothing is happening with the partitions.  I also have ran a gparted live cd and when I hit "apply" it says an error occured and could not repartition.  Is there something that I'm missing:confused:   I seems that I am "prevented" from doing anything to the drive.

Now in xp, I am unable to access some files, saying "denied access".  Any suggestions.  Should I take my revolver to xp?:)  Thanks guys.

---

### Post by Bartender on 2006-12-31
You gotta love it when a plan comes together.  
Any details on the GPLCD error message?  If you already have 3 primary partitions (all the stupid Dell stuff) that might be holding you up.  If GPLCD sese 3 primary partitions already it won't let you create another one.  You should be able to create an extended partition.  Have you tried that?  

I hate Dells.  Some people have gotten rid of the recovery partition (only if you have a copy of that on CD!!)  and then were able to move forward.

---

