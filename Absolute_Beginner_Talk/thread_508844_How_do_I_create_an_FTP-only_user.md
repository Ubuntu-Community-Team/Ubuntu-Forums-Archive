---
title: "How do I create an FTP-only user?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by mattc58 on 2007-07-24
Howdy Friends,

I've just installed VSFTPD on my server and all is working well.

However, I'd like to have a user who is able to login and upload files via FTP but who is NOT able to login via SSH.  How do I do that?  I've tried setting the shell to /bin/false using usermod but that's then disallowing FTP.

Any ideas?

Thanks,

Matt

---

### Post by mattc58 on 2007-07-24
Fixed it.  The issue was that "/bin/false" needed to be in my "/etc/shells".

---

