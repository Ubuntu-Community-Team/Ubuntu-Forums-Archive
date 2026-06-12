---
title: "Manual partitioning"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Enigmaman on 2008-01-25
I want to install Linux as opposed to running it from Live CD.

However I want to retain Windows and dual boot. 

At the moment I have these partitions:

free space                                            57MB
/dev/sda1  ntfs  /media/sda1              88240MB
/dev/sda2 ext3  /media/sda1              68730MB
/dev/sda5  swap                                2969MB

I think the sda1 partition contains Windows.

How should I go about manually installing Ubuntu please?

TIA

---

### Post by taurus on 2008-01-25
I assume you run it from the LiveCD.  Just click on the install icon on the desktop and when you get to the partition screen, pick manual and tell the installer to mount /dev/sda2 as / and format it to ext3.  The installer should know /dev/sda5 swap and mount it accordingly.

Remember, you need to tell the installer to mount /dev/sda2 to / or it will complain that there is no root filesystem.

---

### Post by Aurora@FleetBuzz on 2008-01-25
You may want to make a home partition as well.  Here's a couple of links that helped me when I was planning partitions for a manual install.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)

---

