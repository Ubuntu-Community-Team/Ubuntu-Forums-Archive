---
title: "How to start FTP"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Russellvg on 2007-03-17
Who do I start an FTP on my server???

---

### Post by scxtt on 2007-03-17
have you installed any FTP daemon packages?

i use proftpd myself ... **sudo aptitude install proftpd**

---

### Post by newlinux on 2007-03-17
another good option is still openssh-server and use sftp. Pretty secure, and setup is trivial.

---

### Post by Russellvg on 2007-03-19
I alrdy have open-ssh, how do u start sftp?

---

### Post by newlinux on 2007-03-19
if you have installed openssh-server (make sure it's the server) on the macine you want to ftp into  then you can sftp to that machine with the sftp command (which works just like ftp). If you want a GUI ftp then you can use gftp (make sure to tell it to select sshs from the FTP dropdown). You'll probably need to install gftp from the repos. There are also other options that can do sftp.

---

### Post by scxtt on 2007-03-19
only "problem" w/ that is anyone who wants to "FTP" in will have to have an (ssh enabled) account on the box ...

---

### Post by outofnicks on 2007-03-19
If you have an FTP daemon installed (proftp, vsftp, to name a couple) the GUI way at least for me in Dapper is in the System menu under Services. FTP appeared there after I installed vsFTP.

---

