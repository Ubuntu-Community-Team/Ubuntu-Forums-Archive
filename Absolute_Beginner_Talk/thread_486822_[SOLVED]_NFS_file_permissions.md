---
title: "[SOLVED] NFS file permissions"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by lledurt on 2007-06-28
I am sorry I ask a bunch of newbe questions.

I was able to get my NFS to work but I am having trouble accessing the files.

I have 2 computers one laptop running 6.10 (client) and one desktop running 7.04 (NFS server).  Both computers have the same users and groups with the the same group and user id's manually configured on each machine.

I am sharing a directory family with 770 permissions owned by root with the group of parents.  I can not access it on the client.  When I change ownership to me, I am able to access it on the client.

Does NFS have issues with groups or am I missing something between the computers.  Both have the same identical line in the /etc/group file.

Please help and send me in the right direction.

P.J.

---

### Post by Seisen on 2007-06-28
This might help you out.

[https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29]("https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29")

---

### Post by lledurt on 2007-06-28
Thanks for the reply,

That explains why my group permissions are not working. I am in more than 16 groups when you add up cups, admin .... 

Do you know if running LPAD or NIS will fix the group permissions?  I hate to do that because I am on a small network but if it will work I am up for the challenge.

P.J.

---

