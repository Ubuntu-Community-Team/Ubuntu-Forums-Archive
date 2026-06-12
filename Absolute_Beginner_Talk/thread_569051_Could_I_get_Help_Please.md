---
title: "Could I get Help Please?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by savasalim on 2007-10-06
Hello

I am new to this site and also to linux

I ahve looked around in this forum but can not find the solution to my problem

I have a pc with XP and one with Ubuntu conected to same router

i am trying to FTP access the linux from Xp so i can send and recieve files ETC

i have opend ports 21 & 23 and forwared to ip of Linux.... will not do it

Could anybody PLEASE explain the steps i need to take to achieve this?

Thanks in advance

Savas

---

### Post by mivo on 2007-10-06
Do you have an FTP server running on the Linux box?

---

### Post by savasalim on 2007-10-06
sorry mate i dont even know how to do that :confused:

thanks for the quick reply

---

### Post by talby on 2007-10-06
I prefer samba for windows fileshares, check out 

HOWTO: Setup Samba peer-to-peer with Windows
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by trak87 on 2007-10-06
As mivo suggests, you have to have something on the Linux box to connect to. By default, there is no FTP *server* program installed in Linux. You have to install one. You can also transfer files between boxes with the Samba (smb) networking programs.

---

### Post by mivo on 2007-10-06
I would not recommend to install an FTP server on a Linux system unless you know what you are doing (there are several packages if you really want one, like proftpd). There are some security issues to consider -- would be slightly better to set one up on the Windows system. I'd go with samba as recommended by the other guys. See also "Places -> Connect to Server" in Ubuntu.

---

### Post by Jimmyfj on 2007-10-06
You can install vsftpd on your Linux box. Open a terminal Programs>Accessories>Terminal and enter this code:

```
sudo apt-get install vsftpd
```

Then on your Windows box you can install Filezilla, or another FTP client to access your server.

Be aware that if you leave VSFTPD as default install you have enabled anonymous login.

Edit the file /etc/vsftpd.conf 

```
sudo nano /etc/vsftpd.conf
```

set anonymous login=NO

Then set "local_enable" to YES
and "write_enable" to yes too

Save the file by pressing Ctrl+O + Enter
exit the file by pressing Ctrl+x

You need to remember that the user logging in at your "server" must exist on the system with a valid user name and password. Create a user for access to your FTP server and use that for file transfer. 

This is one way of doing it :) But unless you know what you are doing you should read some HOWTO's about the subject before making the install.

---

### Post by savasalim on 2007-10-06
thanks guys

i ahve tryed samba and vsftpd and still no luck :mad:

I mean i dont want to leave ftp open all the time...Just for 10 mins or sumthing....IS there no easier way?

whats SSH do? 

Can someone please advice/?

Or is there any other way for sum1 to take control of my linux pc Harddisk from outside my network?

Thanks in advance

Ssv

---

### Post by n3tfury on 2007-10-06
you're getting in over your head with ftp . you don't need it for what you want to do, so forget ftp and forget ssh. 

what didn't work in samba?

---

### Post by trak87 on 2007-10-11
You can use the windows Putty utilities to send and receive files from linux to a windows or from windows to a linux box.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

