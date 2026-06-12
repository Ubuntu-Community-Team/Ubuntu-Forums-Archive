---
title: "Root on 6.06 desktop and ftp access"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by inetmug on 2007-03-07
Howdy All,

so far I love ubuntu!

A few questions.  I have 6.06 desktop.  

On the root issue:

I enabled root via sudo passwd root, and it said everything was ok.  But then I went to install the VM tools, but when I did a su to root, it said I did not have permission since I was not the owner of /media/cdrom0 (but the dialog said root was the owner).  I was always under the impression that root could do anything anywhere, but it has been awhile since I worked on unix.  Also, it said I could not log into root from the initial screen - what is up with that?

On the FTP issue:

when I do a ftp ftp.iona.com is says "host name lookup failure", do I need to point it to an initial dns somewhere?


Thanks.

---

### Post by milton1 on 2007-03-07
root should have access, if not, change permissions on cdrom0.

ftp problem does sound like a dns error. often your isp's default gateway can also be listed as dns server.

---

### Post by inetmug on 2007-03-07
On the root issue with media/cdrom0, root is the owner, but there is no write permissions as it is a read-only file system (which makes sense to me now).  Is seems that you can put an iso image there ok as a virtual CD.

On the DNS, how do I set the DNS?

---

