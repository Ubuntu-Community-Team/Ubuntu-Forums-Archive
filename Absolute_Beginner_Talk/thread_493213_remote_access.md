---
title: "remote access"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by ggnewman on 2007-07-05
I am incharge of updating the web site of my son school who is using linux plateform as their server and there are two porograms, webmin and apache server. The question I am trying to ask is : I have a laptop that is using window plateform  how do I access into the server and maintain the system and also most important to upload and download files for the web site remotely. Does my laptop have to be configure too to be able to access into the server or can I just use window explorer to do all these

---

### Post by Raineer on 2007-07-05
Do you need GUI access?

I maintain my website remotely via openssh and vsftpd.  It's just terminal access and ftp but it works for what I need to do and extremely easy to setup.  "VNC" is a tad more complex but not terrible. Let me know, if you need gui I'll post how to do that.

---

### Post by dca on 2007-07-05
I use PuTTY from a Vista laptop to remote access RHEL boxes...???
 
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by ggnewman on 2007-07-05
> **Raineer said:**
> Do you need GUI access?

I maintain my website remotely via openssh and vsftpd.  It's just terminal access and ftp but it works for what I need to do and extremely easy to setup.  "VNC" is a tad more complex but not terrible. Let me know, if you need gui I'll post how to do that.
How do I access through open ssh.?

---

### Post by Raineer on 2007-07-05
As a Windows XP client I use [ZOC Version 5]("http://www.emtec.com/zoc/").  For the server side the package name is ```
openssh-server
``` in the standard Ubuntu repositories.

I had a good guide as to how to set it up, I'll look for the link.. It's a pretty straightforward procedure.

edit: [Here]("https://help.ubuntu.com/community/SSHHowto") ya go

---

### Post by ggnewman on 2007-07-05
Thanks for the guide help. I will give it a try. Do I have to configure on the server side too. and if so how to??

---

