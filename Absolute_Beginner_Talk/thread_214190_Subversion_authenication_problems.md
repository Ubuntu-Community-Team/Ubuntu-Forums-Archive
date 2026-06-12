---
title: "Subversion authenication problems"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Opsive on 2006-07-12
Hello,

I installed Subversion by following [these]("https://help.ubuntu.com/ubuntu/serverguide/C/version-control-system.html") instructions and that went smoothly.  I then installed TortoiseSVN on my Windows machine, and when I went to go check in a file it asked for a username/password.  I found [this]("http://svnbook.red-bean.com/en/1.1/ch06s03.html#svn-ch-6-sect-3.2") page which explains the authenication.  I changed the settings in svnserve.conf and created the users file, but I'm still not able to login with TortoiseSVN.  I've tried restarting both the Ubuntu machine and the Windows machine, but that didn't help anything.

Anybody have any advice?
Thanks

---

### Post by compbrain on 2006-07-15
> **Opsive said:**
> Hello,

I installed Subversion by following [these]("https://help.ubuntu.com/ubuntu/serverguide/C/version-control-system.html") instructions and that went smoothly.  I then installed TortoiseSVN on my Windows machine, and when I went to go check in a file it asked for a username/password.  I found [this]("http://svnbook.red-bean.com/en/1.1/ch06s03.html#svn-ch-6-sect-3.2") page which explains the authenication.  I changed the settings in svnserve.conf and created the users file, but I'm still not able to login with TortoiseSVN.  I've tried restarting both the Ubuntu machine and the Windows machine, but that didn't help anything.

Anybody have any advice?
Thanks


Hi,

If you are using SVN with apache, svnserve.conf will not have any effect. Users and groups should be controlled through apache authentication and authorization. In the first guide you linked to, the bit that references htpasswd, and '/etc/subversion/passwd' should be what your after.

---

