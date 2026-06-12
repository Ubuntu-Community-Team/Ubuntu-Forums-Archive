---
title: "FTP files between two computers."
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Frak on 2007-03-24
Hello, I am trying to FTP files between two computers, both running Ubuntu, ones a laptop, and the other is a Desktop, they are both wireless going through a residential gateway, would anybody know a simple command to initiate an FTP transfer, or a program, or anything else?

Thanks in advance

---

### Post by Bachstelze on 2007-03-24
To transfer files with FTP, you obviously need a FTP server running on one of the machines... I recommend vsftpd.

---

### Post by Frak on 2007-03-24
OK, and from there?

---

### Post by digitzero on 2007-03-24
Once you have an FTP server running and started on the host machine, then you'll need to determine it's local ip.  You can this by running 'ifconfig' from cmd line.  Should be something similar to: 192.168.0.2

On your other computer you can ftp via the command line by typing:

ftp 192.168.0.2

From there you can run some commands such as: cd, ls, get, put, etc

Or you could do it through nautilus I suppose.

---

### Post by Lord Illidan on 2007-03-24
Or Places->Connect to Server.

Any reason why you're not using smb? I use it myself, very nice.

---

### Post by jakev383 on 2007-03-24
> **Frak said:**
> Hello, I am trying to FTP files between two computers, both running Ubuntu, ones a laptop, and the other is a Desktop, they are both wireless going through a residential gateway, would anybody know a simple command to initiate an FTP transfer, or a program, or anything else?

Thanks in advance

I would personally rsync the files. 
rsync -avz -e ssh /dir/to/be/sent user@192.168.1.2:/dir/to/be/sent/to
You'll need the ssh server running on the machine you want to send the files to, though:
sudo apt-get install openssh-server
rsync will send the files, and if you run the command again later will only send new files or files that have changed. Rather efficient.
Hope that helps.

---

