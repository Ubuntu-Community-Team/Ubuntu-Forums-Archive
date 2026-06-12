---
title: "ftp server wont connect"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Stomstedt on 2006-10-20
My ftp server was working fine yesterday or so but now it isn't working... When I try to connect i get an error that says cannot connect.

---

### Post by taurus on 2006-10-20
I think this is like the fourth message that you have started regarding your proftpd!!!  If you can't get proftpd to run again, remove it and try vsftpd.  It's in the repos and real easy to set up.  I have it running on my Dapper in the office...

---

### Post by bswilson on 2006-10-20
> **Stomstedt said:**
> My ftp server was working fine yesterday or so but now it isn't working... When I try to connect i get an error that says cannot connect.

Friend, your post doesn't have **_near_** enough information here for anyone to help you!

[LIST=1]
[*]What changed between yesterday and today.  Did you do an udpate, install anything new?
[*]What are the source and destination you're trying to connect from/to?
[*]Are there any ftp daemon error logs you can share that might shed light on what's happening?
[/LIST]

---

### Post by Stomstedt on 2006-10-20
Is there a GUI for this program?

---

### Post by taurus on 2006-10-20
> **Stomstedt said:**
> Is there a GUI for this program?
No but it's real easy to read the /etc/vsftpd/vsftpd.conf...

---

### Post by Stomstedt on 2006-10-20
Mind telling me how to start/stop/restart the server?  Thanks.

---

### Post by taurus on 2006-10-20
If you reboot your machine, it would start automatically if you installed it with synaptic/apt-get/aptitude.

Otherwise, 

```
sudo /etc/init.d/vsftpd start
```

---

### Post by Stomstedt on 2006-10-20
I'm not sure what I am doing wrong but when I try to upload something using vsftpd on another computer it gives me the error:
An error ocurred while copying a file to the FTP Server. Make sure you have permission to put files on the server.
Details:
200 Switching to Binary Mode
227 Entering Passive Mode (209,132,163,189,191,159)
550 Permission Denied

---

### Post by taurus on 2006-10-20
Okay, are you login with your name and are you trying to upload to your home directory?  Look in /etc/vsftpd/vsftpd.conf to make sure you have set permission to upload!  If not sure, paste it here and maybe I can spot it for you.

---

### Post by wieman01 on 2006-10-20
_Two things:_

A. There is a GUI for "proftp" called "gproftpd".
> sudo apt-get install gproftpd
...to install it.

B. Have you configured your firewall (IP tables) sometime between yesterday & today? E.g. installed a tool called Firestarter?

---

