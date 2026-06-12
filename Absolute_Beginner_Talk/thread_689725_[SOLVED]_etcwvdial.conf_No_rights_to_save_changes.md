---
title: "[SOLVED] /etc/wvdial.conf No rights to save changes"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by mormor on 2008-02-06
I think I am closer than ever to seting up my Huawei e220 hsdpa modem. But I cant save changes to /etc/wvdial.conf as I do not have the rights. 

(opened in text editor to change it btw)

What should I do to get the necesairy rights.?

---

### Post by lloyd_b on 2008-02-06
> **mormor said:**
> I think I am closer than ever to seting up my Huawei e220 hsdpa modem. But I cant save changes to /etc/wvdial.conf as I do not have the rights. 

(opened in text editor to change it btw)

What should I do to get the necesairy rights.?

Use the "sudo" command to get the necessary permissions.  For example, if you're using the "nano" editor, the command would be
```
sudo nano /etc/wvdial.conf
```

For GUI based editors (such as "gedit"), use the "gksudo" command instead
```
gksudo gedit /etc/wvdial.conf
```

Note: Either way, when prompted for a password, enter your normal password.

Lloyd B.

---

