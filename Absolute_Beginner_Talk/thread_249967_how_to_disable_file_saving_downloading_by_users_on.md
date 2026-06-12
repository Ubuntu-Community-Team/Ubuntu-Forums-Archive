---
title: "how to disable file saving/ downloading by users on client machines"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by nanbudh on 2006-09-03
hi everybody, i am looking for an alternative for windows for my client machines in college computer lab. i have a strong feeling ubunto is the right thing. for the moment i want to know is there any way to force users on client machines to save their documents like downloads etc **only on local LAN server machine**? this way i could administer things easily besides user can log from any client.
Please bear with me if this seems trivial.Thanks a lot in advance

---

### Post by csy on 2006-09-03
you could just mount the homedirectory from the server

this way all personal data gets stored in the server and the client wont be touched assuming they have normal userrights

additionally all personal settings are available whereever they choose to login

---

### Post by Scorpuk on 2006-09-03
I think the command for doing the above is something like:

```
sudo useradd username -p your_password -d /path/to/server/home/user
```

Again best to get a second opinion as I am adjusting other posts to suit your situation.

Oh and rememebr to create the folder before you execute the command :biggrin:


Got my info from here : [http://www.ubuntuforums.org/showthread.php?t=79588](http://www.ubuntuforums.org/showthread.php?t=79588) where it helped me create an ftp server.

---

### Post by Miademora on 2006-09-03
Thats correct. Make sure the server is mounted via fstab before the login. Nfs would be one option.

---

