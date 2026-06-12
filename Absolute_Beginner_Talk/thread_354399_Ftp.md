---
title: "Ftp"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-02-05
Through my ISP I have some space where I can upload files, images, etc, and then link to them elsewhere. I use a simple FTP program on my windows machine to upload. What simple and effective FTP software is available for Dapper Drake or is there already something in the OS that I have overlooked?

---

### Post by taurus on 2007-02-05
```
sudo aptitude update
sudo aptitude install gftp
```
Applications -> Internet -> gFTP

Nautilus can upload files to your ftp server too.

---

### Post by tonyr1988 on 2007-02-05
Here's a few:

[http://www.usinglinux.org/ftp/](http://www.usinglinux.org/ftp/)

:) For starters, you could try gFTP. It's fairly straight-forward and simple:

> sudo apt-get install gftp

You can also do Places -> Connect to Server and select FTP.

If neither of those suit your needs, there should be *something* on that list to help you out.

---

### Post by paydaydaddy on 2007-02-05
I got gftp up and running. It works fine for one sight that I upload to, but it will only accept 4 digit passwords. That seems absolutely silly. If I use it for my second sight I will have to change passwords unless I'm missing something.

---

### Post by jimrz on 2007-02-05
> **paydaydaddy said:**
> I got gftp up and running. It works fine for one sight that I upload to, but it will only accept 4 digit passwords. That seems absolutely silly. If I use it for my second sight I will have to change passwords unless I'm missing something.

mine works fine with various sites and passwords are 7 to 9 characters for those sites...are you sure  that it is not accepting more characters rather than simply displaying only 4 at a time in the gui p/w box?

---

### Post by paydaydaddy on 2007-02-06
I just closed the program and then restarted it and it worked fine. The forum comes through again! Yeah.:guitar:

---

