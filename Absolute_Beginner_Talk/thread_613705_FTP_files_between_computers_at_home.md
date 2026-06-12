---
title: "FTP files between computers at home"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by medphys on 2007-11-15
Hi all,

I have been trying to send files to my other computer at home via gFTP.  Prior to the update to 7.10 I was able to do it.  After the update the connection is refused.  I can ping the other computer but cannot ping with the IP address and :21(port 21).

I have tried to look the problem up on the internet but no help so far.  

Has anyone out there have any ideas what to turn on in Ubuntu to make gFTP work?

Thanks for your help.

---

### Post by taurus on 2007-11-15
Have you installed at least an ftp server like ssh-server, vsftpd, or proftpd?

---

### Post by medphys on 2007-11-15
No I have not.  I do not think I did that for the previous version.

---

### Post by Dr Small on 2007-11-15
I find it best to setup proftpd as the server, then get gproftpd for the GUI of proftpd, of where you can setup the users, upload and download speed, directories and whatnot. It's very easy to setup.

Dr Small

---

### Post by Beggar on 2007-11-15
are you sure this isnt an ip-tables problem?

---

### Post by Inxsible on 2007-11-15
you definitely need to set up a ftp server to be able to transfer files. you should also open the ports in Firestarter like Beggar suggested.

---

### Post by hyper_ch on 2007-11-15
install a ssh-server   -->  no configuration needed and it works.

---

