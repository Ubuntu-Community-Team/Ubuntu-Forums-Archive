---
title: "Linux Shell Software?"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by josebalius on 2005-10-12
Hello guys,

I have a script at Sourceforge. In order to use their servers and upload stuff, ect. They give you this:

shell.sourceforge.net

In windows I have a program that connects to shell servers but acts just like an FTP. Anybody know where I can something like this but for Ubuntu?

Thanks

---

### Post by ubuntumaneh on 2005-10-12
it is not so clear, but if you want to use some ftp program, try ftp or lftp.

---

### Post by josebalius on 2005-10-12
Are those programs names or commands?

---

### Post by ubuntumaneh on 2005-10-12
try:

man ftp
man lftp

you can use both in a shell script.

---

### Post by matthew on 2005-10-12
Here is one way out of may to connect via ssh. You will probably want to do some more searching to get an in-depth look, but this will get you started.

If you just want to make a direct connection you can use the file manager in Ubuntu: Nautilus. Go to Places->Computer. A file window will open showing your / directory. Go to Go->Location and then put in:
```
ssh://shell.sourceforge.net
```
You will be asked if you want to connect and then for your login info on sourceforge. Then you should be browsing sourceforge through the Gnome file manager.

---

