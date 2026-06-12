---
title: "umask (vsftpd)"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by repeat on 2006-05-22
Hi,

can anyone explain 'umask' for me?
How does this work, and how to set it right?

In my case I  know it has something to do with permissions for uploaded files and folders... (in vsftpd)

Is it possible to set different umask for different users? (in vsftpd)

Example:
An upload user should have read permission only to the files/folder uploaded (by that user - it could be a shared user account)

A normal user should have something like 751 to their own directory and to the files/folder they upload.

---

### Post by Iowan on 2006-05-22
From [http://www.er.uqam.ca/nobel/r10735/unixcomm.html:](http://www.er.uqam.ca/nobel/r10735/unixcomm.html:)
> umask - establishes the file-creation permissions mask. Usage is 
umask xyz 
The system subtracts x, y and z from the owner, group and other file permissions that it would otherwise assign to new files. This is a shell builtin. 


---

