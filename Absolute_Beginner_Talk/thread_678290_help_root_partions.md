---
title: "help root partions"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-01-25
k this is my 3rd thread so help me to give you some help I'll post a screen shot well I have a few partions already I've backed my precious data up to some dvd's now I wnt linux mint 4.0 its basically ubuntu with a cool take I used wubi to get away from this but its too unstable first I understand partion basics but things like root file system boot partions blahh blahh blahh escape me I dnt want to use basic installer because it doesn't resize well and it will only go down to a 60gig install I wnt bout an 8gig I have my partion situation how too's are for people with one partion and no understaning I wnt somthing easy but not for stupid people and plz dont post just to rack up your posts help me!!!

---

### Post by exneo002 on 2008-01-25
hey what does use largest continuous free space mean?

---

### Post by wormser on 2008-01-25
It is a little hard to understand what you want.  I think you want an 8G partition for an Ubuntu install?  What is the /dev/sda5 fat32 partition for?

This is what you need to do if I am understanding you.

1.  Delete /dev/sda5 and /dev/sda7 partitions.
2.  Create a new ext3 partition for 8G this will be for the Ubuntu install.
3.  If needed create the Fat32 partition again with remaining space.
4.  Install Ubuntu on 8G ext3 partition.  You will need to designate it as root partition.  Select /.  Root is /.  Then it will install.

---

### Post by scorp123 on 2008-01-25
@ exneo002:

Please use some punctuation and structure your sentences. Your current style of writing is not really fun to read.

---

### Post by exneo002 on 2008-01-25
hey thanx I'm putting linux mint on my box now 4 months of my life hell yea

---

