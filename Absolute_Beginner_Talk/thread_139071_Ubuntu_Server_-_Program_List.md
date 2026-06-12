---
title: "Ubuntu Server - Program List"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-03
Hello Everybody !!!

I have read a lot about Setting up an Ubuntu Server...

But I can NOT correlate which programs do what...

From past Ubuntu Threads, I have managed to make the following list:...



_An Ubuntu Server can act as_:

1. Backup Server,	("samba", "cron"

2. Databases,		("mysql", "Postgre", 

3. DHCP Server,	(

4. DNS Server,	("bind9", other DNS: 	[http://cr.yp.to/djbdns/other.html](http://cr.yp.to/djbdns/other.html), 

5. File Server,		("samba", "NFS" for sharing files, "netcat" for sharing files, 
                               "cryptcat", "scp" - Firefox?, 

6. FTP Server,		("vsftpd" supports secure sockets layer, "proftpd" supports 
                                secure sockets layer?, 

7. Mail Server,		("winmail" – has IMAP - what is that?, 

8. Print Server,	(

9. Web Server,		("apache2",  "php5", 

10. Others (what else could it be?)

11. Remote Desktop	("VNC" viewer, "sshd", "ssh" for a Terminal Emulator, 

12. GUI		("X", 


_Question_:

Do l have ALL the above correct?


At the same time, I have also found, the following programs:

"ftp", "pop3", "postfix", "ProFTP", "IpCop", "webmin", "perl", "CMS packages", "samba" (... it can be configured as a "PDC" – what is that?, what is an IDAP installer script?), "DocMan", "pageant" (works as agent to setup the "private key"), ...

But I can NOT correlate which programs do what...

_Questions_:

1. In which category of the above listed, do these above programs belong to?

2. Are there any more programs out there, that I do NOT know of?

3. Let us all make a nice & helpful list here! 


Thanks.

P.S. > At the same time please answer my questions... wherever you see the "?" sign...

---

### Post by Pragmatist on 2006-03-03
Besides getting an education on servers, what exactly are you trying  to do?

---

### Post by dvarsam on 2006-03-05
First I am trying to learn...

Then I will try to put the stuff I learn into practice...

So, these are just basic Questions...

You see, in the Windows Environment, I never had this LUXURY to really Learn!!!

So, I basically need your help people...

Thanks.

P.S.> Besides, for you it is basic stuff, isn't it?

         I am not asking you to solve my problems, just give me some of your 
         EN-LIGHT-MENT in this...

---

### Post by jamesr on 2006-03-05
I hope that you understand that the server install under Ubuntu is NOT a server install, it should be called a basic install. The installation sets up a basic system to which you have to add all of the options. It can act as all of those or some of those depending on what you add. 

I am currently setting up "an archival file server".
Note my server will console only

 1) install basic software
 2) setup basic system as you would like it
3) add samba so that that I setup a shared directory for all to see across the network (windows PC first). This will be replacing a failing NT system.
4) correct all errors
5) add printing capability
6) mod samba to use 5
and so on.

Currently I am doing 2 and 3. 
2 to fix the floppy mount problem , scsi CD-rom problem
3 base check out of samba ( I have not used samba before so this could be slow)

---

### Post by Pragmatist on 2006-03-05
1. Server Backup: many choices. read this: [http://www.tldp.org/LDP/lame/LAME/linux-admin-made-easy/server-backup.html](http://www.tldp.org/LDP/lame/LAME/linux-admin-made-easy/server-backup.html)

2. Databases: Again, many choices, but mysql is a good one.
3. DHCP Server: dhcp3-server  is one of many choices (ok, I'm going to stop saying that)
4. DNS Server: BIND
5. File Sharing: lots of choices. SAMBA for Windows-Unix or Unix-Unix. NFS for Unix-Unix
6. FTP server: vsftp
7. Mail Server: sendmail, exim, postfix, courier, cyrus21, dovecot, etc...
IMAP definition: [http://www.faqs.org/docs/Linux-HOWTO/Cyrus-IMAP.html#ss2.1](http://www.faqs.org/docs/Linux-HOWTO/Cyrus-IMAP.html#ss2.1)
8. printer server: SAMBA smbclient
9. WebServer: Apache is by far the most popular and their are many many more. Roxen is also opensource and high-powered. thttpd is lightweight for small websites.
10. 
a. Proxy Server: squid
b. Remote Configuration Tool: Webmin Too much to list. Linux is geared to be a server so there's lots of tools

11. Remote Server: VNC, ssh (openssh)
12. GUI: X.Org, XFree86 are the only non-commercial options I know of.

> "ftp", "pop3", "postfix", "ProFTP", "IpCop", "webmin", "perl", "CMS packages", "samba" (... it can be configured as a "PDC" – what is that?, what is an IDAP installer script?), "DocMan", "pageant" (works as agent to setup the "private key"), ...

1. ftp and ProFTP are file transfer programs.
2. postfix is a mail server and pop3 is a mail transfer protocol
3. ipcop is firewall software
4. webmin is for remote configuration/administration
5. perl is a scripting language it is most frequently used to write small scripts that tie larger programs together.  However, it is also used a great deal on its own.
6. CMS: Content Management Software.  It's purpose is to, um, manage content.  For example, if you have 1000s of web pages and you want to control how they look collectively, you would use this (like CSS for HTML)
7.SAMBA is used to allow windows and linux to play nicely since they have difference filesystems.  PDS means Primary Domain Server.  It has to do with DNS.

8.IDAP: Internet Data Access Presentation
> The Simple Object Access Protocol (SOAP) specification for Oracle Streams AQ operations. IDAP defines the XML message structure for the body of the SOAP request. An IDAP-structured message is transmitted over the Internet using HTTP(S).

9. DocMan: Document Manager.  It allows you to have multiple people using the same documents and keeps track of all changes, etc..etc..
10.pageant: [http://sourceforge.net/docman/display_doc.php?docid=761&group_id=1#pageant](http://sourceforge.net/docman/display_doc.php?docid=761&group_id=1#pageant)

> At the same time please answer my questions... wherever you see the "?" sign...

**For the future: Try [www.google.com/linux](www.google.com/linux)  and  [www.tldp.org](www.tldp.org)**

---

