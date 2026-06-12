---
title: "Accessing ubuntu shared folders on Windows XP"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by eekfonky on 2007-04-24
I have recently networked my computers and good old ubuntu can read the folders that have permission on my Windows XP computer. However when I share folders with SMB for use with my Windows XP computer it asks me for a user name and password?

I never set it up to do this and cannot access my folders even when I use my login username and password (which happen to be the only ones on my ubuntu system)

Can anyone help as it's driving me nuts

---

### Post by akudewan on 2007-04-24
Post your /etc/samba/smb.conf file here.

Make sure you have set the Security as "Share", _available = yes_, _guest ok = yes_, if you have come across these options somewhere...

---

### Post by jkeyes0 on 2007-04-24
Have you set up your smbpasswd yet?

```
sudo smbpasswd -a USERNAME
```

Once you've done that, the username and password you will use from XP are your Ubuntu username, and the password you set in the smbpasswd from that command.

---

### Post by eekfonky on 2007-04-24
Thanks, I didn't realise I HAD to set up a password. Followed your instructions and it worked a treat!!

Thanks for the help

---

