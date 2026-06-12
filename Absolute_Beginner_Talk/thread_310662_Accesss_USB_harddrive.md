---
title: "Accesss USB harddrive"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Slurm on 2006-12-01
Hi Everyone,  

I recently bought a Maxtor 200gig USB external harddrive to use to backup my machine (AMD 64 using Dapper).  When I plug it in to the USB port, the OS recognizes it and an icon appears on my desktop which I can open fine.  However, when I try to copy folders onto it,  I get the message "You do not have permission to write to this harddrive'  I cannot figure how to give myself permission.  When I hit Properties, and try to give read and write permission to the harddrive I get this same message.  

Can someone give me a command I can to give permssion?

Thanks

---

### Post by steve.horsley on 2006-12-01
I'm not sure how to fix that the "proper" way. it may involve setting up an entry in /etc/fstab with the option **umask=0**.

A quick and dirty way round it is to use gksudo nautilus to give you a root privilege file manager.

---

### Post by Slurm on 2006-12-01
Thanks,  

I just tried this but it says I cannot do this because the drive is 'read-only'.  Now where do I go?

---

### Post by steve.horsley on 2006-12-01
Odd. Can you post the output of the command:
**mount**

---

