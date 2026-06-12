---
title: "Permissions Problems Apache/File System"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by theMaab on 2007-11-09
I've recently setup an Ubuntu box running Apache2 in our office for a internal website.

My problem now is when I transfer the files for the site from my laptop to the web root on the Ubuntu box I run into permission problems when trying to view the site.

What is the ideal way to get files to the web server?

I was trying to use my USB drive to transfer them, but should I have an FTP server?

I really get confused with the permissions.

I was finally able to do so by creating a shortcut on the desktop with the command 'gksudo nautilus' and then copy the files to /var/www .

I then had to chmod 777 on those files, and that was a pain cause it didn't seem to get the sub directories.  I was even using the -r for recursive.

Any ideas on how I should have this setup to make it easy, but still be somewhat secure would be greatly appreciated.  This box just run on the internal network, so security is not that bad of an issue.

Thanks in advance.

---

### Post by Daveski on 2007-11-18
What owner and group are the OK files on the web server? You will need to make sure the user who is used to copy new files to this location has the same group. If you are using an FTP server or a Samba server you can usually set a default owner and group on all files being received.

---

