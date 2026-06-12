---
title: "partition please help"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-06-24
ok guys i need help .. im installing ubuntu on my frnds comp along xp .. i.e. dual boot.. now im on the partition part but im stucked.. i selected manual partition and..

[[IMG]http://img156.imageshack.us/img156/2734/screenshotaz5.th.png[/IMG]](http://img156.imageshack.us/my.php?image=screenshotaz5.png)

this is where i am stuck ^.. i already created a 10 gega space .. i select it and click new partition, i put mount root in (/media/sda2) and then click forward but then i get this error

"No root file system is defined.

Please correct this from the partitioning menu."

can anyone please help me, thanks !

---

### Post by HunkieChan on 2007-06-24
nevermind, i google searced it and i found it.. i just need to put forward slash in mount root ..thats it , thanks guys

---

### Post by HunkieChan on 2007-06-24
guys.. how i do create a swap ? help,p lease

---

### Post by cogadh on 2007-06-24
Create another small logical partition from the free space you had for "/" and make it about twice the system RAM. Choose swap for the format type, that should do it.

---

### Post by HunkieChan on 2007-06-25
but there is no option to create another one..

---

### Post by cogadh on 2007-06-25
When you create the first one, leave some empty space behind, don't set it to use the entire free space.

---

### Post by HunkieChan on 2007-06-25
oh cool got it but whats primary/logical and beginning/end.. whats for what ?

---

### Post by cogadh on 2007-06-25
Hard drives have a limit of up to four primary partitions that can contain a bootable OS. However, one of those four partitions can be set up as "extended" which allows it to further subdivided into any number of logical partitions. Logical partitions cannot contain a bootable OS, they can only hold additional data. See [this page]("http://www.pcguide.com/ref/hdd/file/structPartitions-c.html") for all the boring details on primary, extended and logical partitions.

The beginning/end references have to do with where on the physical disk within your drive each partition is placed. In your case, you'll want your primary partition to start at the beginning of the free space on the drive but limit its size to leave some space at the end of the drive. That space will need to be set up as a logical partition to contain the swap file.

---

### Post by HunkieChan on 2007-06-25
i actually did right away. thanks anwyay bro

---

### Post by az on 2007-06-25
> **HunkieChan said:**
> ok guys i need help .. im installing ubuntu on my frnds comp along xp .. i.e. dual boot.. now im on the partition part but im stucked.. i selected manual partition and..


Why manual partitioning?  The default works just fine and you don't have to worry about making a mistake and blowing away your system.

---

### Post by cogadh on 2007-06-25
The default takes over the first primary partition on your first drive. In my case, that was the Windows partition and I wanted to keep that for dual-booting, just as HunkieChan is trying to do. If you are trying to do anything other than install Ubuntu as the sole OS on a machine, you might have to do a little manual manipulation of the partitioning.

---

### Post by HunkieChan on 2007-06-25
for swap i had logical and end, for the other one ext3 i had primary and beginning, i think it was ok

---

### Post by az on 2007-06-25
> **cogadh said:**
> The default takes over the first primary partition on your first drive. In my case, that was the Windows partition and I wanted to keep that for dual-booting, just as HunkieChan is trying to do. If you are trying to do anything other than install Ubuntu as the sole OS on a machine, you might have to do a little manual manipulation of the partitioning.

By default, if there is sufficient space on your drive, you are offered the option of shrinking the partition and dual booting.

If you have sufficient space and are not offered that option, something is wrong.  Try defragmenting your windows partition and try again.  There is no need to do manual partitioning to dual-boot.

---

