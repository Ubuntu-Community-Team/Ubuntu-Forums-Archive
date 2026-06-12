---
title: "Partition Problems - 7.04"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Tommy James on 2007-04-24
Doing a clean install of 7.04 and having a challenge with manual partitioning.  Seems there is a bug with creating partitions over 200GB (there is already a bug report listed).

Since I have a 250GB HDD I need some advice and thoughts from the group.  Idealy, I would have a 30GB /, 218GB /home, and 1.5GB swap.

Should I do the guided partition install and add /home after the install?
Should I increase / to 50GB?
Should I set up more partitions like /boot and /usr (I'm a newbie so I've never had a seperate partition for them and need help understanding why, what size, and what do in the future with upgrades and new installs etc)?

Thank you for your time!!!!

---

### Post by Pisi-Deff on 2007-04-24
You could do what I did. Just make that 218 GB into 2 partitions: 1 for /home and another one for some more data(for example a partition for movies).

---

### Post by louieb on 2007-04-24
Are you using the Live or Alternate CD? Just currious.

If you create a separate /home then 10 gig is plenty for / (root).
Separate /home is nice in time of trouble and reinstall is needed. 
Placing other directories in there own partitions is a server kind of thing and a pain in the rear to figure out how much space to give each.

> ***Pisi-Deff :***    You could do what I did. Just make that 218 GB into 2 partitions: 1 for /home and another one for some more data(for example a partition for movies).  Separating your data from the installation is also a good idea. Keeps it out of the way and safe during  upgrade and reinstall time.

---

### Post by Tommy James on 2007-04-24
Using the LiveCD, never thought about trying to install with the Alternate CD.  Should I  download and give it a try?

On the separate data partition, what would that be called (/xxxx) and I'm guessing I'd still have a /home partition?

---

### Post by Pisi-Deff on 2007-04-24
> **Tommy James said:**
> On the separate data partition, what would that be called (/xxxx) and I'm guessing I'd still have a /home partition?
You could mount it everywhere you want. For example it could be on /data or /home/data or /media/data or /mnt/data etc... 
Yes, you'd still have a /home partition, because that's where your usersettings and configurations would be.

---

### Post by Tommy James on 2007-04-24
Thanks Pisi-Deff,

What size would you make /home and /data?  /data would be used for documents, pictures, movies, etc similar to the My Documents idea?

For backing up, I need to copy /home and /data now correct?

Thanks again!

---

### Post by wldstrm on 2007-04-24
If you still are having partition problems try downloading and burning a standalone Gparted live cd.  I had partitioning problems yesterday when i was using the xubuntu live cd and when i used the gparte live cd everything worked like a charm.

---

### Post by Pisi-Deff on 2007-04-24
> **Tommy James said:**
> Thanks Pisi-Deff,

What size would you make /home and /data?  /data would be used for documents, pictures, movies, etc similar to the My Documents idea?

For backing up, I need to copy /home and /data now correct?

Thanks again!
Well, since you can't make a partition over 200GB and you need to use up 218GB... I would give 20-25GB to /home and the rest to /data
Yes, if you want to backup your stuff, then you need to copy both /home and /data. :)
I'm glad I could help. :)

---

### Post by Tommy James on 2007-04-24
GREAT THANKS!  I'm off to install 7.04!!!!  I love this stuff!

---

