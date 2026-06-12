---
title: "Terminal help"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by P0CKETS on 2008-02-29
How do I change the @ubuntu part in pockets@ubuntu:~$ in terminals?

---

### Post by Dr Small on 2008-02-29
Edit:
```
/etc/hostname
```

And once you chacge it, simply logout and back in for it to take effect.

Dr Small

---

### Post by Whiffle on 2008-02-29
You don't want to edit /etc/hostname I don't think.  

[http://www.ducea.com/2006/08/07/how-to-change-the-hostname-of-a-linux-system/](http://www.ducea.com/2006/08/07/how-to-change-the-hostname-of-a-linux-system/)


Do you want to change the hostname of your computer or just change how your terminal prompt looks?

---

### Post by Nythain on 2008-02-29
and google "bashrc" or "change bash command prompt" for ideas and suggestions on how to change what the prompt says entirely :P

---

### Post by P0CKETS on 2008-02-29
Says permission denied. I even tried to navigate there in a root terminal?

---

### Post by P0CKETS on 2008-02-29
Yes, I want to change the host name.

---

### Post by Nythain on 2008-02-29
```

gksu gedit /etc/hostname

```
woudl be how you would want to edit the file

---

### Post by P0CKETS on 2008-02-29
Thanks a bunch! :)

---

