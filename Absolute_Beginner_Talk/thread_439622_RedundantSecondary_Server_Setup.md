---
title: "Redundant/Secondary Server Setup"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by zeroaim on 2007-05-10
Hi, 

A colleague has been asking me what we can do if one of our servers was to stop working. We currently have one computer running Ubuntu 7.04 Server. 
What i would like to do is have a secondary server running that is configured almost identically to the primary server. If the primary server was to fail i would like to have the secondary server up and running within a short period of time (approx 1/2 -1 hour).
What would be the easiest way to accomplish this?

Thank you.

---

### Post by [S|G] on 2007-05-10
That depends a lot on which services your're running. If you have (mostly) static data such as web pages the easiest way would be to create an image from the primary server and restore the image on the secondary server (dd can handle the task pretty well and should be simple if they're identical).

If you run services such as a database server or samba domain controller, you should probably be running some sort of replication between the two servers at all times so that in the event of the primary server failing the secondary would have the same data.

---

### Post by dacool25 on 2008-05-01
Sorry to bring this post back from the dead, but how would you set up the back up server so it would know to take over.  Would you just set it to have the same IP as the master server (Which would cause an ip address conflict), and when the master failed, the backup would automatically pick it up?  Or is there a better way of doing this?

Thanks.

---

