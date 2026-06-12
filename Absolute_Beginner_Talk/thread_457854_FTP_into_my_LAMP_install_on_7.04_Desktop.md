---
title: "FTP into my LAMP install on 7.04 Desktop"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by esoterica on 2007-05-29
I followed these instructions (which could be a little clearer, but did get me finally up and working)...
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Using the terminal window and these commands...

aptitude install apache2

aptitude install php5-mysql 

aptitude install libapache2-mod-php5 

aptitude install mysql-server

and followed all the other instructions on that page as closely as they could be deciphered. Everything does seem to be working finally! I can see both web pages and my testphp.php file from other computers on my LAN. However, I still some some simple questions I can't seem to find any further info on and was in hopes someone here can please point me to the documentation I need.

My first question I'll start with is how do I make an FTP connection into my web server to upload web pages from another PC on my LAN?

I know how to make an FTP connection to a web server, but it doesn't seem to be working here, I start up my ftp program on my other computer and try to connect to the LAN IP address of the web server and can't get a connection. Is there an FTP service that actually has to be installed still on the Apache2 server, because I haven't done so (like I said, just followed the above documentation so far). 

I'd preferably like to be able to make an SFTP connection to the entire computer as root, but for now I'd be happy just being able to ftp into it so I can copy some web pages over from another computer on my LAN.

I can't find any Ubuntu documentation though that tells me how to set this computer up to allow the SFTP connection into it as root (or even the simple non root ftp connection, which isn't what I want, but anything would be better at this point).

I have more questions, but would like to get this first one solved.

---

### Post by ukripper on 2007-05-29
Have you tried Proftpd ?

Check here:
[http://ubuntuforums.org/showthread.php?t=79588&highlight=proftp](http://ubuntuforums.org/showthread.php?t=79588&highlight=proftp)

---

### Post by esoterica on 2007-05-29
No I have not, I haven't tried anything other than those instructions on the LAMP install. I'm trying to do all of this the Ubuntu way rather than the normal Linux way I already know how to do most things (which would mean this frustrating to adapt to "sudo" stuff would be gone in a minute). I'll go and check out your link right now though, thanks in advance for a suggestion.

---

### Post by esoterica on 2007-05-29
Isn't there some type of default way to SFTP into a normal Ubuntu LAMP install if I had used the Ubuntu LAMP server installation instead of the desktop. I guess what I'm asking is, had I have just done the Ubuntu LAMP server install instead of 7.04 desktop, how would a person upload files to this server? There must be something I'm missing because what the hell good is a web server you can't sftp into to upload files on as the site administrator?

I appreciate those instructions, but that how to is from 2005, I'm paranoid about doing things documented that long ago when usually there are newer and better ways of doing things. On my live public CentOS Linux Apache server I have ftpd that's installed. Is there some Ubuntu friendly documentation to install and configure something like this specifc to an Ubuntu server?

What are people running live Ubuntu based web servers using to handle their sftp on these servers in 2007?

---

### Post by ukripper on 2007-05-29
I know that howto is old but if you go through the thread you would get all the information you need to know about FTP and how to configure regardless of the app you want to use. However, wherreas LAMP stack is concerned I am currently using XAMPP for testing my web apps and if you are talking about uploading files to localhost then you just have to save your files to public_html (which in my case is linked to XAMPP's htdocs) shows up when I enter //localhost/username, all my saved php files i  can browse are in here

However refering to apache docs I came across this, might be helpful in your case:

[http://httpd.apache.org/docs/2.0/howto/public_html.html](http://httpd.apache.org/docs/2.0/howto/public_html.html)

---

### Post by Bachstelze on 2007-05-29
> **esoterica said:**
> 
What are people running live Ubuntu based web servers using to handle their sftp on these servers in 2007?

SFTP is basically FTP over SSH. For it to work, you need to have a SSH server installed :

```
sudo apt-get install openssh-server
```

---

### Post by esoterica on 2007-05-29
HymnToLife,
I was hoping you'd find this post!

Here's some weirdness, I never directly installed OpenSSH or even OpenSSL for any of this (I do think I installed gnupg which may have had something to do with this), yet, when I run my testphp.php file it's showing I already have all of these things like OpenSSL etc.. instaled, that doesn't help me one bit though with the FTP, (SFTP) portion, as OpenSSH doesn't contain any type of ftp server I can use, it's just the encryption portion.

It looks like I'm going to end up having to compile pure ftpd into this from source code, which means I may as well then just remove the entire Ubuntu packaged install of everything and compile my APache, PHP and MySQL from source while I'm at it since easy updates are already going to be out the Window.

This has me thinking I may as well just scrap my entire Ubuntu install and go with a different flavor of Linux like CentOS or Debian since the only reason I went with Ubuntu in the first place was the hope of easy updates from the manager.

I'm finding it hard to believe though they don't already have a package option available for Ubuntu like pure ftpd or something up to date with some documentation so I don't have to read through 11 plus pages of posts that started in 2005 when a single documentation page created in at least 2006 should be available somewhere.

I'm finding this hard to believe, there has to be some up to date information in the Ubuntu documentation somewhere, they offer a server platform, people are using the server platform in the real world, so they have to be sftping into the thing somehow. Even if I were to use pureftpd for this, how do you use a program that requires root access to connect when Ubuntu doesn't support a root user? This is all so strange for me to get use to.

---

### Post by esoterica on 2007-05-29
I knew there had to be some good Ubuntu documentation somewhere on this. I was looking too hard for it, it was right under my nose the entire time.

[https://help.ubuntu.com/7.04/server/C/ftp-server.html](https://help.ubuntu.com/7.04/server/C/ftp-server.html)

---

### Post by NumberOne on 2007-05-29
In my opinion, proftpd with gproftpd is a lot eaiser.  gproftpd is a graphical interface to proftpd.  No editing of config files needed. All is done from gproftpd.  It all installs right from synaptic.

---

### Post by ukripper on 2007-05-30
> **NumberOne said:**
> In my opinion, proftpd with gproftpd is a lot eaiser.  gproftpd is a graphical interface to proftpd.  No editing of config files needed. All is done from gproftpd.  It all installs right from synaptic.

Depends if you are really used to the traditional linux way(through terminal and configs) GUI will seem different, just a matter of preference. However, bottom line  is proftpd/gproftpd is one of the best and secure ftp server which works well with your firewall(if you have any in place) and NAT.

---

