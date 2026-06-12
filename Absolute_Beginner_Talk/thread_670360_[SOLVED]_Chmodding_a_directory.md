---
title: "[SOLVED] Chmodding a directory"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Jadd on 2008-01-17
Hello everyone. I can't understand why running this command:
```
sudo chmod =rwxr-xr-x ubuntu-black/
```
doesn't change the root permissions to read write execute, group permissions to read and execute, and others permissions to read and execute. Instead, it changes it to his (according to ls -l)
```
d-w------- 2 root  root  4096 2008-01-17 17:19 ubuntu-black
```

Thanks in advance!

---

### Post by Cypher on 2008-01-17
Try
```

sudo chmod 755 ubuntu-black

```

---

### Post by Jadd on 2008-01-17
Thanks. I just tried that, and got:
chmod: cannot access `ubuntu-black': No such file or directory
So I tried it again, and it worked! Thanks. Any idea why I'm getting this weirdness?

---

### Post by tigerplug on 2008-01-17
Make sure its in your path ;)

---

### Post by Jadd on 2008-01-17
:) of course it's in my path! I didn't do anything in between except an ls to make sure I wasn't dreaming that the directory existed. Do you think the problem's got to do with the trailing slash?

---

### Post by PeterJS on 2008-01-17
Capitalization maybe?

---

### Post by Jadd on 2008-01-17
Nope, 'cause I used the auto-complete tab feature, then backspace to get rid of the slash the first time, and the second time I just used the keyboard shorcut up.

---

### Post by Jadd on 2008-01-18
Do you think it has anything to do with using PAM for automatic encryption?

---

### Post by Jadd on 2008-05-16
I am almost certain this is because of PAM's automatic encryption, I have to use sudo -i, but that works, so I guess I can mark this as solved.

---

