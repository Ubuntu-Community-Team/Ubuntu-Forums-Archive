---
title: "file permissions in xfce"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-07
Hello forum people,

i am using xfce desktop here...it's an Ubuntu distro

when i right click a file to change it's permissions, the option to make the file executable is missing..

how can i set up xfce so that this option becomes available?

shell files and things...

thanks

Vince.

---

### Post by aysiu on 2008-04-07
How were those files created?

---

### Post by vinceUUUU on 2008-04-07
Hello

uh....i got the files by download from the international network...internet

the person that created the files was a program maker...Dave,

He wrote a program for Linux...(a scripts) and offered it up for free inside these forums

is that any help?

Vince

---

### Post by jkeyes0 on 2008-04-07
It's been a while since I've used Xfce, but you should still be able to open a terminal up, browse to the directory containing the file, and type
```
chmod a+x FILENAME
```
(where FILENAME is the exact name of the file, with proper capitalization and file extension). This will make it executable for all users.

---

### Post by vinceUUUU on 2008-04-07
Hello

thanks jkeyes

that worked fine

Vince

---

