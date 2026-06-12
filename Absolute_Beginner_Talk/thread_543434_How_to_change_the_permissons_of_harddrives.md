---
title: "How to change the permissons of harddrives"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by chatterjee on 2007-09-05
I don't have the write permission to any of the hard drives except for the one on which Ubuntu is installed.I'm using an administrator account.Why is it happening?

---

### Post by conjur3r on 2007-09-05
You're going to have to be more specific than that.  What partition?  Where?  And also output the permissions on the mount point.

---

### Post by hyper_ch on 2007-09-05
(1) You should not be using an administartor account

(2) Here's a short read on file permissions: [http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)

You normally have only write access to your /home/USER folder for security reasons. If you mount other harddisks, you will have to give yourself permissions to access it. Let's assume you have a harddisk mounted at /media/hdb1 and your username is "chatterjee". Then you could *chown* that folder to your user:

```

sudo chown chatterjee.chatterjee /media/hdb1

```

That would set the /media/hdb1 folder to your user- and groupname and you could access it.

---

### Post by chatterjee on 2007-09-05
*chown  *is working quite well.But can it be reversed in the present session?And I'll be glad if you clear your first point.

---

### Post by hyper_ch on 2007-09-05
You could change the file permissions totally... as I have no idea what you want to do you need to read upon Linux file permissions/ownership yourself and decided what the best approach is to you... maybe you need to alter the settings in fstab to accomodate your needs.

---

