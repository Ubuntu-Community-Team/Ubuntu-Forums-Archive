---
title: "Ok, I installed FTP now what?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by hfnd on 2008-04-04
I installed FTP on my Ubuntu server with a second NTFS formated hard drive for storage on my Windoze home network. I want to be able to retrieve these files away from home. I opened the port on my router. What next?

---

### Post by tamoneya on 2008-04-04
you should be all set to get files externally so you should go to a friends house and test it.  Also i would recommend installing a ssh server ```
sudo apt-get install ssh
``` This will give you shell access to your computer in case you need to do any administration.

---

### Post by bodhi.zazen on 2008-04-04
First, learn to secure it.

Second, if you have a router forward the ports.

Third, if you like, you can use a graphical client like gftp or any number of firefox plugins.

---

