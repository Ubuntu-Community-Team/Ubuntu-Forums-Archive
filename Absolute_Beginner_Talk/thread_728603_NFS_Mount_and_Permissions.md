---
title: "NFS Mount and Permissions"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-03-19
i have an NFS share set up on /var/www on my server.  I mount it to /home/titan/www on my workstation. If i change the folder permissions on my local workstation they change on the server.  I have tried making a www-data group and adding myself to it but that doesnt work and i cant write the directory.  Any suggestions?

---

### Post by Xiong Chiamiov on 2008-03-19
I'm a little confused about what the problem is.  Perhaps there is a typo and you meant to say that the permissions *don't* change on the workstation when you change them on the server?

---

### Post by The Titan on 2008-03-19
no, they do change.  Maybe im just retarted but it is a pain.

server share, "/var/www"

local mount point "/home/titan/www"

what i want to do is change the local owner of the mount point and have it not change the owner of /var/www.  Does that make more sense?

---

### Post by herbster on 2008-03-19
Can you paste the exact command and output you're using to change permissions?

---

### Post by The Titan on 2008-03-19
chown titan:titan /home/titan/www

the issue is that that also changes /var/www to titan:titan on the server

---

