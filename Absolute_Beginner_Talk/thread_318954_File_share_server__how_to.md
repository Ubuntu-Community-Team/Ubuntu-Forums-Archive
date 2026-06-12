---
title: "File share server : how to?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Linux Lover on 2006-12-14
I am not much aware about the servers and its installations. Presently I have bought another computer and with my previous 2 pcs., presently I am having 3 pcs. in my home. I want to make them connected through a LAN. The infrastructure is ready and working.

All the PCs have its own network card, and the server have two different network cards. It is already connected. The server contains WinXP and the nodes are connected with Win98. All these connections were done by the AMC guys who are providing support to the machines. I am now thinking to switch over to Linux server and want to learn the job. The main purpose of the server is to sharing files and operating internet from different nodes.

I am now planning to replace the system with Ubuntu, instead of Win. Please let me know how do I proceed. Any tutorial before starting the job will be highly appriciated. 

Also note that I have ubuntu 6.06LTS (Desktop) in my hand. Is it mandatory to install a Server version for such a file sharing server? If it requires, then I have to shift to Fedora Core 6 for the server and Ubuntu to other two nodes. Please guide me.

---

### Post by outofnicks on 2006-12-14
Just install Apache, MySQL, and PHP from the Package Manager and you have a server setup, known as LAMP--then share files by HTTP or FTP.

---

### Post by Linux Lover on 2006-12-15
Thank you for your help. Should I have to install Apache, MySQL and PHP to all the nodes and to the server or only to the server?

Also let me know after installing those how to connect (or open port) from server to nodes? Please treat me a newbie and tell me in detail.

---

### Post by outofnicks on 2006-12-15
I am somewhat of a newbie myself, and the Apache install has very good documentation, available in Synaptic Package Manager as "apache-doc". 
There are other file sharing solutions for you besides LAMP, perhaps SAMBA will work better--it is file sharing with Windows computers. You will have to do some research on this, as I have not gone into that area. I use Apache, MySQL and PHP as a testbed for websites, and FTP is my preferred method of moving files from one computer to another on a local network that is not exposed to outside infiltration because it's easy to setup and use.
It all depends on what you need to do, there are other options besides mine and hopefully someone else will offer them here.
If you want to try Apache, just open the Package Manager and check either apache or apache2, along with apache-docs --you don't need MySQL or PHP for only  a basic HTTP server, and Apache is not even necessary for FTP. For that you only need an FTP server program running in the background on the computer you want to access, and on the other computer an FTP client such as gFTP or my favorite, FireFTP--a Firefox extension acting as a full FTP program. Examples of FTP servers are proftpd, ftpd, and .WU-FTPD--all available from the Package Manager for an easy install.

---

### Post by hyper_ch on 2006-12-15
Use samba :)

give the linux server with the samba installed a fixed IP address in the LAN

and then alter to /etc/samba/smb.conf to something like this:

```

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2006/09/29 19:14:58

[global]
workgroup = WORKGROUP
hosts deny = 10.0.0.1

[exchange]
comment = Exchange
path = /home/Exchange
force user = smbuser
force group = smbuser
read only = No

[appz]
comment = Appz
path = /home/Appz


[MP3]
comment = MP3
path = /home/MP3

```

workgroup --> Your windows workgroup name
hosts deny = the IP of the router (I don't want outside connections)

[exchange]  --> "an RW folder where everyone in the lan can write to"
comment  --> The name
path --> where it is located
force user --> I'd use the default user that you setup when you installed ubuntu
force group --> see above
read only --> allow writing

[appz]
comment --> see above
path --> see above

[MP3]
comment --> see above
path = --> see above


Once that is done, you need to add users to samba:

```

sudo passwd USERNAME

```

with that you can add (different) users to samba... you will then be prompted to enter the password (for the connection) twice


Once that is done restart samba: 

```

sudo /etc/init.d/samba restart

```

and then go to a windows machine, go to the network "environment" (I don't know what it's called correctly in english), add a new network ressource and enter the following:

```

\\IP_OF_THE_SERVER\Exchange

```

Repeat that... maybe you don't have to... if you are connected once and gave correct login and stuff then you may browse also the other shared folders with Windows Explorer

---

