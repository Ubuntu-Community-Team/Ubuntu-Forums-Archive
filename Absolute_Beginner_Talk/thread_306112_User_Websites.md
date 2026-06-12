---
title: "User Websites"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by macuserx1 on 2006-11-24
I recently installed Ubuntu LTS on an old Compaq (2.4Ghz, 512 RAM) running headless and have been trying to teach myself how to administer a server through SSH. I have used other Distros in the past (CentOS, OS X, Solaris) so I am not a completely new user. One thing that I cannot seem to grok in Ubuntu is how to let each user have a website. The only directory that has web access seems to be /var/www. So I guess I have two questions:

1:How would I go about setting up apache so that every user can have a personal website at [http://localhost/~username/?](http://localhost/~username/?)

2:How can I set up the FTP server so that each user only has access to their own home folder using vsftpd?

Ultimately I would like to set up this machine as a server to offer free shell accounts/web services to people that would like to learn about linux, and for myself as well.

Thanks in advance!

---

### Post by woro2006 on 2007-04-26
a2enmod
pick userdir
then create public_html to look like ~/user/public_html

---

