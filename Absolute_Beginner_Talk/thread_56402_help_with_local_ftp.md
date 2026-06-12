---
title: "help with local ftp"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by servvs on 2005-08-12
i dont know exactly how to check what my default ftp username and password are. i tried to connect under an anonymous connection and it said connection closed by remote host. i tried my username and password and got the same error. i tried root and its username and got the same error. does anyone know what that error means, or what my default username and password is for ftp.

---

### Post by KingBahamut on 2005-08-12
[QUOTE=servvs]i dont know exactly how to check what my default ftp username and password are. i tried to connect under an anonymous connection and it said connection closed by remote host. i tried my username and password and got the same error. i tried root and its username and got the same error. does anyone know what that error means, or what my default username and password is for ftp.[/QUOTE]
 which ftpd are you using?


proftpd is probably the easiest to setup and maintain.

---

### Post by PeP on 2005-08-12
[QUOTE=servvs]i dont know exactly how to check what my default ftp username and password are. i tried to connect under an anonymous connection and it said connection closed by remote host. i tried my username and password and got the same error. i tried root and its username and got the same error. does anyone know what that error means, or what my default username and password is for ftp.[/QUOTE]

** 1. what is your ftp Server? **
plz give us a hint!

** 2. is your ftp server running? **
did you check that?


** 3. did you tried to connect from the same machine **
to verify that it is not a firewall issue


** 4. Did you enable anon login? **
then have you tried 
login: anonymous 
or login: ftp 
the anonymous login sometimes require an email adress (just any is ok) as a password, depending on yyour configuration, most time any password will be ok.

** 5. if you allowed user login **
it is the same login/password than the *nix account

** 6. you do not understand anything from the language used above **
read the man pages and howtos first

** 7. you are still lost **
post the conf file (remove anything personal like ip addresses, servername ... and replace it with a dummy random informations)
for proftpd:
/etc/proftpd.conf
for vsftpd
/etc/vsftpd.conf

---

### Post by KingBahamut on 2005-08-12
Beat me to the punch PeP

---

### Post by servvs on 2005-08-12
[QUOTE=PeP]** 1. what is your ftp Server? **
plz give us a hint!

** 2. is your ftp server running? **
did you check that?


** 3. did you tried to connect from the same machine **
to verify that it is not a firewall issue


** 4. Did you enable anon login? **
then have you tried 
login: anonymous 
or login: ftp 
the anonymous login sometimes require an email adress (just any is ok) as a password, depending on yyour configuration, most time any password will be ok.

** 5. if you allowed user login **
it is the same login/password than the *nix account

** 6. you do not understand anything from the language used above **
read the man pages and howtos first

** 7. you are still lost **
post the conf file (remove anything personal like ip addresses, servername ... and replace it with a dummy random informations)
for proftpd:
/etc/proftpd.conf
for vsftpd
/etc/vsftpd.conf[/QUOTE]
 the thing is... my monitor for my linux box is busted. so i have to connect through ssh. is there any way i can turn on a ftpd through ssh?

---

### Post by KingBahamut on 2005-08-12
apt-get install proftpd 

configure at /etc/proftpd.conf

then run proftpd at commandline 

verify its running via commandline , using top 

then try to login to it.

---

