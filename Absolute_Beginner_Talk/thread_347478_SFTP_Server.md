---
title: "SFTP Server"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by RED WIND on 2007-01-27
What software do you recommend for a SFTP Server

---

### Post by taurus on 2007-01-27
sshd.

---

### Post by Xappe on 2007-01-27
```
sudo apt-get install openssh-server
```

---

### Post by RED WIND on 2007-01-27
where do I go to change the settings on it

---

### Post by taurus on 2007-01-27
Look in /etc/ssh especially /etc/ssh/sshd_config.

---

### Post by RED WIND on 2007-01-27
is there a pages on how to config this

im a noob when it comes to linux

---

### Post by taurus on 2007-01-27
Usually the default for sshd is good enough when you install it.  What do you plan to do anyway?

[http://www.openssh.org/](http://www.openssh.org/)

---

### Post by RED WIND on 2007-01-27
well I want to have usernames passwords and home folders so I can give friends it and we can share files

---

### Post by taurus on 2007-01-27
Why not just create a regular account on your machine (BUT don't put him on the adm & admin or he will be able to use sudo) and he can log in or ftp to your machine.  And if you want, create a share directory like /opt/shares and you two can share stuff from there.  That way, he won't mess up your $HOME directory and you won't destroy his $HOME directory (unless he upsets you).

---

### Post by RED WIND on 2007-01-27
he is a windows person so he cant log in (that I know of) and I want to do FTP but I want to do the secure FTP incase someone finds out about it or just stumbles apon it

---

### Post by RED WIND on 2007-01-28
How about a normal ftp server b/c that is just too hard for me to configure

---

### Post by taurus on 2007-01-28
You mean something like vsftpd or proftpd.  What exactly do you intend for your friend to do with your machine?  You just want him to upload/download stuff to/from your machine and that's it.

---

### Post by steve.horsley on 2007-01-28
Give your windows friend a copy of filezilla. 
That does sftp. 
[http://filezilla.sourceforge.net/](http://filezilla.sourceforge.net/)

You will still need to create an account for him on the Ubuntu box. His filezilla will be able to see the same files as he would see if he logged in with a  shell. If your friends want to share a directory full of files, they could all use the same username, or all belong to the same group and use group permissions to see in each other's home folders, or just all write in /tmp which is writeable by everyone.

---

### Post by morningboat on 2007-02-06
You are probably interested in an easy to configure FTP server with security features, right? 

For personal usage, I'd recommand you to have a look at CrossFTP Server 
[http://www.crossftp.com/crossftpserver.htm](http://www.crossftp.com/crossftpserver.htm)
which supports Implicit/explicit SSL/TLS encryption, and its configuration is quite easy thanks to its GUI interface. 

Almost all FTP clients support FTP over SSL/TLS, and it is often a safer choice over SSH in case of the attacks.

---

