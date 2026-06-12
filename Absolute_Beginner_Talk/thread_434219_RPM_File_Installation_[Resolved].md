---
title: "RPM File Installation [Resolved]"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by mb01915 on 2007-05-05
I want to install Novell's iFolder.  The installation file is a rpm file and I cannot seem to find any way to install it.  Need help.

---

### Post by aysiu on 2007-05-05
Read this:
[http://psychocats.net/ubuntu/installingsoftware#rpm](http://psychocats.net/ubuntu/installingsoftware#rpm)

---

### Post by Acglaphotis on 2007-05-05
Use alien

```
sudo aptitude install alien
```

then

```
alien -d  /path/to/rpm/
```

-Acgla

---

### Post by mb01915 on 2007-05-05
Thanks.  I followed the instructions from the link and  it supposedly installed - I can't seem to find the program anywhere in the applications menu.

---

### Post by Acglaphotis on 2007-05-05
Try running Ifolder from terminal.

-Acgla

---

### Post by mb01915 on 2007-05-05
How do I do that?

---

### Post by Sef on 2007-05-05
Check System > Preferences > Main Menu.  Once you find it, just click on it, and it will show up in the applications menu.

---

### Post by mb01915 on 2007-05-05
I am in this forum because I am a beginner.  I can find the terminal.  How do I run a program from the terminal.

---

### Post by Sef on 2007-05-05
> I am in this forum because I am a beginner. I can find the terminal. How do I run a program from the terminal.

```
gksudo ifolder
```

---

### Post by mb01915 on 2007-05-05
Thanks.

---

