---
title: "mount home folder different hdd"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by gnw23 on 2007-10-30
i have edubuntu server 

I have two queries regarding that

1) i want to mount home folder on different HDD(Primary slave) and all the other edubuntu server and software on different HDD (primary master)

2) i want to know if there is any way in which we can take up an autobackup of the home HDD everyday on third HDD (Secondary Master)

Thanx in advance 

Plz help me with this

Shashikant

---

### Post by jr.gotti on 2007-10-30
Okay...to mount your home dir on a different HDD, the command would be 'sudo mount /dev/hdb1 /home' and everything else would be on hda1. Of course, the numbering/labeling scheme depends on your partitioning scheme. Is your drive partitioned to do this? Your going to need your home HDD partitioned with one partition formatted ext3, and your root HDD, your going to need it to have two partitions, one for swap (2 gigs) and the rest for root (/).

Once all the partitioning is done, you can add the drives to /etc/fstab to have them mounted in the appropriate locations upon boot.

As to your second question, you'll have to set up a cron job. Write a script to perform the backup, and place it in /etc/cron.daily. That way, everyday it will perform. Any questions? Just ask.

I just realized the first part of my answer is confusing. Once I have more information on your partitioning I can elaborate. Good luck!

---

### Post by phyrewall on 2007-10-30
best guide (in my opinion):

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Worked for me with little effort!

---

### Post by gnw23 on 2007-10-31
actually i am really weak in partitioning thing 

i can do it in windows but not in linux 

so i just use default partition that ubuntu gives 

can it work on this

---

### Post by Duck2006 on 2007-10-31
> **phyrewall said:**
> best guide (in my opinion):

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Worked for me with little effort!

+1

---

