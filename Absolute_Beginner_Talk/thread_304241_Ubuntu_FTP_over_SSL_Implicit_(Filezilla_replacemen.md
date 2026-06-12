---
title: "Ubuntu FTP over SSL Implicit (Filezilla replacement)"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by getut on 2006-11-21
Is there any Filezilla type replacement FTP client for Ubuntu?

I need to connect to a server with FTP over SSL (FTPs) and filezilla for windows supports that connection/authentication scheme. In google I found nightly builds for Filezilla for linux and got that working, but the linux builds don't have support for FTP over SSL (FTPs), they only have support for standard FTP and sFTP.

gFTP in the Ubuntu repositories is the same, only FTP and sFTP.

---

### Post by wirelessmonkey on 2006-11-21
Sounds like you want vsftpd! 

sudo apt-get install vsftpd

G'luck

---

### Post by getut on 2006-11-21
Ahh.. thanks for the quick reply. You are correct vsftpd does support FTP over SSL, but it is the FTP server not a client.

I neglected to specify in the first post, but I need a linux client that supports FTP over SSL.

---

### Post by getut on 2006-11-21
Well the windows version of filezilla is working under wine for me and got me connected, so I guess this gets me going.

I prefer a free linux native solution, but all I found was iglooFTP Pro and it is a fee based product. Filezilla in wine will do just fine.

---

### Post by jrjazzman on 2006-11-21
I really missed Filezilla when I switched to Linux.  gFTP and some of the other oft suggested programs are not up to par for my tastes.  I'm primarily using Nautilus right now.  It does ssh, scp, ftp.  You can bookmark sites (file > connect to server).  You might want to check out FireFTP.  It's a firefox plugin and is quite nice.  I hear it can run standalone as well.

---

### Post by lukanova on 2006-12-26
how to compile gftp with ssl support the quick way on debian (and probably ubuntu too):
(this is debian unstable):


# apt-get build-dep gftp
# apt-get install libssl-dev openssl
# apt-get source gftp
# cd gftp-2.0.18     *this is the version number, it's different in time*
# vim debian/rules (or use nano or gedit or some editor)
change the option on 10th or 15th line from
--disable-ssl
to 
--enable-ssl
# debian/rules binary
it should now compile and pack all gftp packages
# cd ..
# dpkg -i gftp*.deb

run gftp and it should have SFTP and SHTTP options

---

### Post by alphpt on 2007-05-27
Worked for me, thanks!

---

### Post by moredhel on 2007-05-27
There is a linux version of filezilla, though it's the version 3 beta....

Just search for it in synaptic.

---

