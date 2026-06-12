---
title: "Stop and start processes"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by joramdam on 2007-04-02
Where do i find this utility in UBUNTU ?

---

### Post by mikeyphi on 2007-04-02
Don't know what you want to do - but is this what you want? - SYSTEM - ADMINISTRATION - SERVICES

---

### Post by joramdam on 2007-04-02
For example how do i restart SMB ?

---

### Post by johnny4north on 2007-04-02
you find them -panel>system>administration>system monitor. others are- sessions and services settings.  Ubuntu 7.04

---

### Post by coxy on 2007-04-02
Or you can do it on the command line, just replace vsftpd with the process you would like to stop, start or restart:

> sudo /etc/init.d/vsftpd restart
sudo /etc/init.d/vsftpd stop
sudo /etc/init.d/vsftpd start


If your working directory is /etc/init.d/ then you can do the following:

> sudo ./vsftpd restart
sudo ./vsftpd stop
sudo ./vsftpd start


---

### Post by joramdam on 2007-04-02
> **coxy said:**
> Or you can do it on the command line, just replace vsftpd with the process you would like to stop, start or restart:



If your working directory is /etc/init.d/ then you can do the following:

Can this be done with a GUI

---

### Post by coxy on 2007-04-02
Yes, but I am not 100% sure how in Ubuntu because I am a Kubuntu user. Some of the above replies look like they answer the question.

You should try it via the command line, it is good practise to get used to it and it can be a very powerful tool when you are familiar with it. Once you are, it is quicker to restart a process through the command line than messing in the GUI. It is also very useful for servers and remote access.

---

### Post by mikeyphi on 2007-04-02
> **joramdam said:**
> For example how do i restart SMB ?

You'll find SMB under SYSTEM - ADMINISTRATION - SERVICES
you'll be asker for your password then you will see the GUI with a list....just tick the icon for SMB and exit

---

### Post by joramdam on 2007-04-02
joramdam@dream:~$ sudo ./smb restart
Password:
sudo: ./smb: command not found
joramdam@dream:~$ sudo ./smb restart

?????

---

### Post by 3rdalbum on 2007-04-02
> **joramdam said:**
> joramdam@dream:~$ sudo ./smb restart
Password:
sudo: ./smb: command not found
joramdam@dream:~$ sudo ./smb restart

?????

Use this block of code:

```

sudo /etc/init.d/vsftpd restart
sudo /etc/init.d/vsftpd stop
sudo /etc/init.d/vsftpd start

```

---

### Post by mikeyphi on 2007-04-02
> **joramdam said:**
> joramdam@dream:~$ sudo ./smb restart
Password:
sudo: ./smb: command not found
joramdam@dream:~$ sudo ./smb restart

?????

It looks as though you are using the command whilst in you Home directory.

If you are going this route rather than the GUI as you initially asked then you need to navigate to the directory where the appropriate file is before using the above command.

Whilst I agree that it might be a god thing to learn how to use the Terminal - it is much easier (in the early days) to use the built-in GUIs.  However don't let me stop your fun!!

---

### Post by coxy on 2007-04-02
It may be called samba, it is on my Debian servers.

> 
sudo /etc/init.d/samba restart
sudo /etc/init.d/samba stop
sudo /etc/init.d/samba start


Using ./samba restart will only work if you are in /etc/init.d/

---

