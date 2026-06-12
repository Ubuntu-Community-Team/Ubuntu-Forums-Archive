---
title: "newbie stuck on installation/partitioning"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by lantana on 2007-10-23
I've recently partitioned my HD with a dedicated 50 gig for ext3. I've now tried to install Ubuntu 7.10 & get to the point where I'm told to prepare partitions [around step 4 in the installation] as "no root file system defined". Any one got a fix or ideas how I can progress?

Ta lantana:lolflag:

---

### Post by Hobbs131 on 2007-10-23
I know when i did mine i had to boot vista first & partition that to 60 & leave the rest free. & then when i installed ubuntu i had to take the free space & partition that for ubuntu.

---

### Post by rudeboyskunk on 2007-10-23
You have to be sure to name the mountpoint as /

---

### Post by jw5801 on 2007-10-23
I tend to just wipe a section of the disk and let the installer create it's own root partition. So delete the ext3 partition you made, and tell the installer to use the "largest contiguous free space" or whatever the option is. Else if you know what drive label it has (ie. /dev/sda1 etc etc) then go to the advanced partitioning setup and use that to set the root partition to a particular existing partition.

---

### Post by lantana on 2007-10-23
Thanks
Currently running Xp pro & When I get to the choice on installation for auto or manual partitioning. Auto offers me  one option only 'to partition the whole 500 gig HD' however on manual it allows me to directly chose my 50 gig ext3 partitioned portion. Once I chose that segment then I get the issue for 'prepared partitions' & 'no root file system defined'

Ta Lantana:lolflag:

I'm very green & need information almost pre-digested & spoon feed.

---

### Post by Hobbs131 on 2007-10-23
make a second partition thats more than 256mb & put that as root. then that error should go away

---

### Post by DocEsq on 2007-10-23
I was having problems too trying to install Ubuntu to the partition that I wanted.  I had tried various methods from the auto resizing to picking the largest continuous free space.  

What I finally did was install an old hard drive that I had laying around and make that as master.  I made my XP drive a slave.  By installing Ubuntu then I used all of the hard drive without any problems with the install.  It also loaded grub automatically so that I am able to choose if I want to start XP or Ubuntu.

I hope this helps.

Doc

---

### Post by lantana on 2007-10-23
Thanks  to all
I deleted my ext3 partition & installed Ubuntu easily onto 'free contiguous space'
Ta lantana:lolflag:

---

