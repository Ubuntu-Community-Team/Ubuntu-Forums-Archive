---
title: "connecting SSH (windows) and Ubuntu"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by thouvou on 2008-03-22
Hi everybody!
I'm new with Ubuntu, until now I was using Scientific Linux (and I didn't have any problems because everything is installed by default).
My problem is that I'm trying to connect my laptop (windows) to my desktop (Ubuntu). I've managed to exchange files with ftp (I've installed vsftpd) but I cannot be connected by using SSH secure shell for doing remote use of the desktop :confused:. Do I have to install any other programs?
Any help?
Thanks in advance

---

### Post by unutbu on 2008-03-22
If you don't have the ssh server running on the linux side, run this:

```
sudo apt-get install openssh-server
```

Make sure sshd is running. If not, run

```
sudo /etc/init.d/ssh start
```

Then edit the file /etc/hosts.allow. Add a line something like this:

```
ALL: windows_ip
```

where windows_ip is either the name of the windows machine or its ip address.
If you want to refer to the machine by name, you should also edit /etc/hosts. Put a line there which looks something like this:

```
192.168.0.1 windows_ip
```

where you'll have to change 192.168.0.1 to whatever ip address is appropriate for you.

---

### Post by chaos315 on 2008-03-22
Hey, thanks for the post, but will this work from say an office computer where the ip can change?
If so, how do you input the changing ip address?

---

### Post by Bachstelze on 2008-03-22
There is absolutely no need to edit /etc/hosts.allow. Unless you changed it yourself, in which case you probably know how to use it, it allows everything.

---

### Post by unutbu on 2008-03-22
Yes, HymnToLife is correct. My mistake. You only need to alter /etc/hosts.allow if you also put something like 

```
ALL: ALL
```

in /etc/hosts.deny.

---

### Post by schneiderman on 2008-03-23
since this seems like a good place to ask, I would like to connect to my ubuntu server from my mac using x11 over the internet. However, I am not sure exactly how to do this. I followed some suggestions on the forums but the server is connected to a router/modem which is connected to the internet. Every time the connection times out. Is there a step that I am not aware of?

Thanks

---

### Post by kevdog on 2008-03-23
Did you port forward port 22 from your router to your computer and either use Firestarter or Guarddog or edit the IPtables manually to allow incoming connections to port 22?

---

### Post by schneiderman on 2008-03-23
> **kevdog said:**
> Did you port forward port 22 from your router to your computer and either use Firestarter or Guarddog or edit the IPtables manually to allow incoming connections to port 22?

afraid not. I'm not quite sure how to do that using only the command line (i didn't install the graphics package)

---

### Post by kevdog on 2008-03-23
For IPtable use, please see this wiki page:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by schneiderman on 2008-03-23
> **kevdog said:**
> For IPtable use, please see this wiki page:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

thanks kevdog

---

