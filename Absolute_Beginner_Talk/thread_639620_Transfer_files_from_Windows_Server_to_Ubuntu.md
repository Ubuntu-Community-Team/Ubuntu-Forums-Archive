---
title: "Transfer files from Windows Server to Ubuntu"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by dewman0012 on 2007-12-13
Hi all,

I am happy to say we are dipping into the linux world at work and have setup a Ubuntu Server. At any rate, we will be hosting one of our sites on this server and I have some questions. This website is currently hosted on our Windows 2003 Server where it is setup and functioning. What I would like to do is move all the files over (PHP and template files) and our MySQL database. How would I go about doing this? 

Thanks in advance! 


We are running:

Ubuntu 7.10 Server Edition w/ GUI
LAMP Install

---

### Post by ^rooker on 2007-12-13
1) About setting it up:
This is mainly distro independent (except for program versions), and there are some excellent HowTo's out there. 

One of them is:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

I've skipped all the mail-server-setup and the ISP-config installation, but I've used it to get quota, MySQL, PHP and Apache up and running in no-time!

It's mostly "apt-get install ..."    :)


2) MySQL administration:
I'm not sure if it's mentioned in that HowTo, but simply install "phpMyAdmin" as soon as your apache is running. It's a breeze. There are also plenty of Howto's about that.

You can also install phpMyAdmin on your current windows server to export a dump of your database - and use it to import it on the Linux Server.


3) Don't bother with using a graphical environment on the server. You won't need it. Your access to the system will be over SSH and FTP.
Tip: Before you've setup an FTP server you can use "FTP over SSH" (sFTP) to transfer files to your home directory - an excellent (Windows/Linux) FTP/sFTP client for that is "FileZilla"


4) When you move existing PHP sites from Windows to a Linux server it's important to check your configuration for the following things:
- DLLs: When you require some non-standard extensions for apache/php, make sure that you will get them for Linux, too. 

- Paths: If you have paths/filenames in configuration files (e.g. config.php pointing to some directory), make sure that you replace them all properly:
* relative paths must have / instead of \
* linux filesystems are case sensitive (!!) - Including code from "Myfile.php" will fail if the file is called "myfile.php". (I've seen this happening...)




It's might seem a bit overwhelming for the first time, but stick to a good howto for your distro version and you'll be fine!

---

### Post by dewman0012 on 2007-12-17
Thanks for the information. So far it is going alright. I have had some issues when it comes to setting up static IP's so I just have to keep searching to find out. I will have to take a look at the filezilla you mentioned.

---

