---
title: "Need some help setting up Samba"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by emes on 2008-04-14
Hi,

I am a new user to Linux / Ubuntu etc. My goal is to setup a file server that users can access remotely and download files via FTP.

I downloaded Ubuntu Server 7.10 and installed Samba. 

That is as far as I got. I know Windows Server but this is all new and I haven't been able to find a site that explains the install procedure, setup, commands, and administrating the server,  etc. 

To be more specific setting up a folder, sharing it, giving rights to certain people. etc.

Is there anyone that has to time to fill me in  on what to do?

Thank you very much.

---

### Post by IcemanV9 on 2008-04-14
emes: Here's a great [[COLOR="Orange"]wiki[/COLOR]]("https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29") on Samba.

---

### Post by K.Mandla on 2008-04-15
Posts split from sticky thread.

---

### Post by HermanAB on 2008-04-15
There is an Ubuntu specific howto guide on the Samba web site.

Cheers,

Herman

---

### Post by Iowan on 2008-04-15
[Here]("http://ubuntuforums.org/showthread.php?t=202605") is another good How-To - but not really geared toward a server. Several "Perfect Server" setups at [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu")

---

### Post by torry_loon on 2008-04-15
For the FTP part I would recommend vsftp.
You can have each user ftp into their own home directory and you can share the home directory using samba.

---

### Post by superprash2003 on 2008-04-15
proftpd is also good.. you could also install the gui for it called gproftpd

---

### Post by freebeer on 2008-04-15
> **emes said:**
> Hi,
My goal is to setup a file server that users can access remotely and download files via FTP.


What am I missing here?  If that's the extent of your goal, you don't need Samba.  Unless I'm missing something from the equation.

---

### Post by tommynz1975 on 2008-04-15
for samba E books in pdf format and other linux books go to
[www.linux-books.us/](www.linux-books.us/)

---

### Post by emes on 2008-04-16
Thanks for everyone's reply. 

Let me restate my question. I am new to Linux. I have been reading a few books on Linux but they were geared to Desktop and not server version.

I have 2 projects that I want to do. The problem I have is that there is no good guide how to accomplish them. So far I have come across 9 versions of Linux and their variations, so that is confusing. Commands are different in some of the versions, more confusion.

Here are the projects:

1. Setup a server that allows remote users to view the files on the server. One user will have the rights to download the files and the other user only to view the files. This will be a standalone network, different IP address than the company network. (So if the server gets hacked hopefully they won't get to the other network.)

That is why I installed Samba. The Ubuntu server software described it as file sharing.

2. Setup a Linux router and add software that monitors / give reports where the user visited on the Web. I would love a suggestion for software for router and monitoring software.

These are the two projects. I would need an explanation as to what Linux software to use and installation instructions, and setup instructions for user rights, creating the directories, and how to copy the files onto the Linux server.

Thank you very much. If anyone lives in the States I would like to call them and talk them on the phone if possible. It would be much faster than emailing back and forth.

Thank you very much,

Emes

---

