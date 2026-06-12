---
title: "Problem with read-only file"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-09-11
I just installed vpnc, which is a vpn program for Linux  with apt-get install. I can open up the file /etc/vpnc/example.conf or the file /etc/vpnc/default.conf as it is sometimes called with vim. The problem is that I cannot write to the file, so that I can set up the vpn settings. I have tried chmod with no success. Any an all help related to changing the permissions properly is greatly appreciated.

Thanks 

:guitar:

---

### Post by Beggar on 2007-09-11
have you checked to see if you are the owner of the file, or if you are a member of the group that owns the file? 

Can we get the output from 

```
ls -la /etc/vpnc/example.conf /etc/vpn/default.conf
```

---

### Post by jprb85 on 2007-09-12
The output I get is 

-rwxr-xr-x 1 root root 388 2007-03-17 15:35 /etc/vpnc/example.conf

but in vim when I try to edit the file, it still says readonly option is set and refuses to let me make changes.

:popcorn:

---

### Post by splintercellguy on 2007-09-12
You have to edit as root:

sudo nano /etc/vpnc/example.conf

or

gksudo gedit /etc/vpnc/example.conf

for a GUI.

---

### Post by jprb85 on 2007-09-12
Each time I try any of those commands it gives me this message.

/etc/sudoers is mode 0755, should be 0440. I do not know what that means.

:lolflag:

---

### Post by splintercellguy on 2007-09-12
Uh oh, did you do something while you were root? To fix this, boot to Recovery Mode and type:

chmod 0440 /etc/sudoers

---

