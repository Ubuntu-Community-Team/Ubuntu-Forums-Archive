---
title: "Symbolic linking for localhost"
date: 2011-06-08
forum: Any Other OS
---

### Post by Pres B on 2011-06-08
Hey everyone... I was trying to set up a symbolic link between my htdocs folder and a folder in my home folder.  

I did:

```
sudo ln -s /home/me/public_html /opt/lampp/htdocs
```

I got this error when I tried to open a page from the home (/home/me/public_html) folder

> Access forbidden!

You don't have permission to access the requested object. It is either read-protected or not readable by the server.

If you think this is a server error, please contact the webmaster.
Error 403
localhost
Wed 08 Jun 2011 11:32:04 PM EDT
Apache/2.2.17 (Unix) DAV/2 mod_ssl/2.2.17 OpenSSL/1.0.0c PHP/5.3.5 mod_apreq2-20090110/2.7.1 mod_perl/2.0.4 Perl/v5.10.1 

I have seen people saying you shouldn't change the permissions on the htdocs folder....I'm the only person who uses this laptop so I'm wondering if that even matters..?  

Any ideas on what I'm doing wrong with my symlinks?  I had it set up before but I crashed my distro and I'm starting from scratch again...

Thanks in advance.

---

