---
title: "hard disk parition"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by ferronica on 2007-06-08
i want to partition my 40 Gb HDD, like C: and D: drive where in C: i would like to install Ubuntu 7.04 and D: drive i would like to use as Data Storage so in future format needed D: drive will remain safe. Is that possible if yes please explain i am new in Linux world  :) :) :) :)


40GB HDD used by only ubuntu no windows :)

---

### Post by daschmidty on 2007-06-08
You could make one partition mounted as "/" (you need this, it is the root filesystem. like C where it contains all of your system files) and then for data make a partition to mount as /home. In linux your /home will hold all of your docs and personal files as well as email profiles etc. Linux avoids driveletters and goes with a tree filesystem where / is the top and everything exists under it with a path starting at /, but these can be multiple actual partitions.

---

### Post by ferronica on 2007-06-08
sorry i didnt get you whatever you said :(  "/" what this for? right now i have ubuntu installed in 40GB HDD, right can i format my ubuntu system file only not home folder

---

### Post by steve.horsley on 2007-06-08
You will need to choose custom partitioning in the installer and make the partitions yourself.  For a 40G drive, I would be inclined to do it something like this:
Partition 1: 9 Gig, Type ext3, mount on "/"
Partition 2: 1 Gig, Type swap, mount on Swap (this is the virtual memory for when real memory is full)
Partition 3: 30 Gig, type ext3, mount on /home

You could possibly create three primary partitions for the job (hda1, hda2, hda3) but it may be more flexible to create an extended partition first (hda1) and then create logical partitions inside that extended partition instead (hda5, hda6, hda7).

You could use the installer to create the partitions, but you may feel more comfortable using a graphical partitioner like Partition Magic or gparted (on the Ubuntu live CD) to creat the partitions before running the installer. You still need to choose custom partitioning in the installer in order to select which partitions to use.

---

### Post by daschmidty on 2007-06-08
"/" Is the root filesystem on unix computers. Unix does not use C:, or D: etc, but rather a single tree. If you were to use drives letters however / is roughly akin to C: in that it holds the basic system information. However in unix / is also the top level of every partition that is mounted. So /home as a data partition would be like having a drive D:, except instead of being it's own entity it would appear as C;\D. It requires a different mental approach to escape the drive-letter frame of mind, but the organization is quite logical once you get the hang of it. for example you cd drive may be E: in windows but in ubuntu it would be /media/cdrom- where it is a filesystem mounted under the root / in a subdirectory called "media"

---

### Post by Malta paul on 2007-06-08
Hi, The answer to your question is Yes, you might like to check out >http://Ubuntuguide.org< Have fun;)

---

