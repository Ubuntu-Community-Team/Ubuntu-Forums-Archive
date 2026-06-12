---
title: "gftp problem"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by bineshb on 2006-12-27
Hi,

I'm getting an error 550/<file name>: Access Denied when trying to use gFTP to transfer a file from Ubuntu to a windows Server.

Any idea how I can fix this.

Thanks.

---

### Post by pseudonym on 2006-12-27
what ftp server are you using on the ubuntu box? is it set up for anonymous login?

---

### Post by bineshb on 2006-12-27
I'm using vsftp for the server which i installed via apt-get. Just checked /etc/vsftpd.conf and anonymous_enable=YES is set.
I'm new to Ubuntu and the linux thing... :)

---

### Post by pseudonym on 2006-12-27
were you accessing the server anonymously? you could try and login as user from the windows machine. obviously make sure that user is specified in the vsftpd config file if it needs to be...

---

### Post by bineshb on 2006-12-27
Hi,

I figured out the problem. The problem was with the destination Windows Server that was used for FTP. Guess the permissions on Win server are improper.

I tried gFTP again using a different destination server for FTP upload and the operation was successful.....

Cheers,
:D

---

