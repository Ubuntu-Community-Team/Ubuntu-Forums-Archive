---
title: "DynDNS FTP"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-10-20
I just got a DynDNS account and im getting the hang of it. Its very easy and very usefull, i was wondering how hard it would be to use my Ubuntu box as a FTP server through DynDNS. If anyone has done this I could really use your help. Thanks

---

### Post by sizzam on 2006-10-28
When I first started using Ubuntu, I started out looking for a good FTP server to run.   After researching, I found that I was better off setting up an SSH server for remote access.  That way I can SSH into my box from remote locations and have terminal access into my box.   I can also "SCP" into my box, which visually acts just like FTP, only it goes over SSH.   

On Windows, I use Filezilla as my FTP client.   Filezilla also supports SCP, so you can use Filezilla to transfer back and forth from your Ubuntu box.

To install the ssh server, all you have to do is:

sudo apt-get install ssh

Then, you will be able to 'scp' into your box using port 22 (instead of 21 for FTP).   Note that your firewall will have to allow access to your box via port 22 for this to work.

On a side note, once you open up your box to allow users to FTP or SCP, you should think about security.   I use a program called 'DenyHosts', it monitors SSH and blocks people after so many failed attempts to try to access my server.

[http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/)

---

### Post by charles.g.moore on 2006-10-28
Try this how-to and once it's set up you can do what you want, I have used this in conjunction with dydns successfully

[http://www.ubuntuforums.org/showthread.php?t=256102&highlight=server](http://www.ubuntuforums.org/showthread.php?t=256102&highlight=server)

---

