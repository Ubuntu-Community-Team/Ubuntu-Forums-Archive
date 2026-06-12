---
title: "Noobish server question"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Tarmon.Gaidon on 2006-03-19
Hi sorry if this is a not so smart question but I was wondering if any one could help me out. as a learning experience I wanted to set up a server on computer i have laying around that i would be able to use for file sharing not only from my house but from anywhere.

Sorry if this is a stupid question but if you could at least point me in the right direction it would be a lot of help.

---

### Post by NeghVar on 2006-03-19
Not sure but the easiest way to connect to it would probably be through a router that supported VPN (Virtual Private Network) but im not an expert.

---

### Post by tim.n9puz on 2006-03-19
You will probably need to do several things to achieve what you want.

First, are you wanting to share files with other Linux machines or with Windows machines using Ubuntu as a file server?

To share with Windows machines you need to run Samba on the Ubuntu box. To share with other Linux machines I believe you need to use "nfs", the networked file system.

Using one of these will let you share files within your local network.

To share files with machines outside your network I assume you mean you want remote access to your files. This can be done with the ssh server on Ubuntu or you could run an ftp server. ssh is more secure and clients are available for Linux or Windows so you can move files to and from the Ubuntu server computer.

We can probably provide a better answer if you share some more details about the kinds of machines, who you want to share files with, etc. :-k 

I have a computer that runs Ubuntu at my home. Any computer on our home network can access it and any external user whom I give an account can access files stored there as well. I do not run a public web or ftp site with it but that is possible too.

---

### Post by IYY on 2006-03-20
The easiest thing to do would be to install an FTP server (search for ftp server in Synaptic, there are a couple of choices). You may also want to install an SSH server so that you can not only access your files remotely, but also login remotely. However, you must understand that both of these things are a security risk to your machine. The best solution is to simply have strong passwords for all of your users. If you have a user named "guest" with the password "guest", you can be sure that your machine will be cracked within days.

I also like to have a name for my machine, so that I don't have to remember my IP. This can be done at [www.no-ip.com](www.no-ip.com).

---

### Post by Tarmon.Gaidon on 2006-03-20
Thanks sorry for being kind for lack of detail. Umm, the computer I am setting up as the server will be running Ubuntu and right now atleast I will be accsesing it from my local windows machine and windows machines remotly. I will probaly be sharing files with a few friends of mine.

---

### Post by alamba on 2006-03-20
ssh is a good bet buddy. However, rather than using FTP, I'll suggest you use scp which is built into the ssh package for ubuntu. There are free client software's available for windows - WinSCP i think. 

This works just like FTP (you can share files between any external machine) however, doesn't have the security issues associated with FTP. That is, unlike FTP it doesn't transmit your username and password in clear text.

A

---

### Post by Tarmon.Gaidon on 2006-03-20
Thanks for the help, my friend and I are going to try it tonight. If i have any problems I will post later tonight.

---

### Post by tim.n9puz on 2006-03-24
I have an Ubuntu based server that's used by several Windows clients. As was mentioned earlier ssh is a better option than ftp in my opinion too. A good file transfer client for Windows that supports ssh is Filezilla. There is also a Windows  client called PuTTY that works well for logging in remotely.

Tim

---

