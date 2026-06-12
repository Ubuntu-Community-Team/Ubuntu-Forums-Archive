---
title: "How to give users space in my server"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by jordi_rc on 2006-10-26
Hello to all.

I am running Xubuntu with Xampp as server and Xoops as CMS.

I need to give my users space to upload their files (jpg, gif, wrl -vrml worlds-, etc). Each user will have his own folder as is usual in all webservers. Each user must only be able to access his folder. 

As I use Xoops as CMS, users would need to ask for web space through my xoops site, and I will add them to an special group (worldbuilders) so they are allowed to send files and have their web space.

I saw that Xampp has ProFTPD as ftp server...

I would like users to access their directory using a web application or their favorite ftp client...

The only problem is that I am new in ftp server and these matters, so I have no idea on how to acomplish all this.
;) ;) :-k 

Can someone give me some ideas or info on how to give web space to my users easily, or give me some forum or url where to learn this?

Thanks.

Jordi

---

### Post by taurus on 2006-10-26
You just create a regular account for each of your user on your server.  Then, install an ftp server like proftpd, vsftpd, etc.  That's it...

---

### Post by jordi_rc on 2006-10-29
Thanks Taurus, but if you would, please give me a more detailed explanation, or better a resource or link to learn how to do this.

Thanks again

Jordi

---

### Post by Bachstelze on 2006-10-29
just *sudo apt-get install vsftpd*. All you'll ever nedd to know will be on the manpages ;)

---

### Post by jordi_rc on 2007-10-12
Thanks

---

