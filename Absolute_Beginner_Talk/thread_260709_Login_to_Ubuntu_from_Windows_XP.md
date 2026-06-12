---
title: "Login to Ubuntu from Windows XP"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by essex on 2006-09-19
Can anyone point to some info on howto login to Ubuntu from Windows XP. The XP box is a wireless laptop, it can see the Linux box but will not accept my username or password. Thanks](*,)

---

### Post by jd65pl on 2006-09-19
What are you trying to use to log in to ubuntu?

FTP
SSH
Samba?

---

### Post by emprog on 2006-09-19
For windows, I believe you can use putty?

---

### Post by Brunellus on 2006-09-19
how are you attempting to access the ubuntu box?

If by ssh, for instance, you need (on the ubuntu box) to install the 'ssh' package
```

sudo aptitude install ssh

```

on the Windows side, you'll need a client.  again, in the case of ssh, I recommend [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

### Post by jd65pl on 2006-09-19
This thread maybe useful to you.

[http://ubuntuforums.org/showthread.php?t=246768&highlight=remote+admin+windows]("http://ubuntuforums.org/showthread.php?t=246768&highlight=remote+admin+windows")

---

### Post by essex on 2006-09-19
How do I find out, SSH Samba or FTP. I was trying to map a network drive using Exploer.

---

### Post by Brunellus on 2006-09-19
> **essex said:**
> How do I find out, SSH Samba or FTP. I was trying to map a network drive using Exploer.
That's Samba.

You'll want to follow the directions here

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

with particular attention to the directions for setting up the Ubuntu machine as a server:

[https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88](https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88)

---

### Post by jd65pl on 2006-09-19
Try [this ]("http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server+howto")for ftp

Try [this ]("http://ubuntuforums.org/showthread.php?t=202605&highlight=setup+samba+server")For Samba

Try [this ]("http://ubuntuforums.org/showthread.php?t=191564&highlight=setup+ssh+server")for VNC server

Try [this ]("http://www.linuxforum.com/linux_tutorials/16/1.php")for SSH server

Thanks

J

---

### Post by essex on 2006-09-19
Thanks to everyone, I will sift through this info. I am sure that I will find my answer. :cool:

---

