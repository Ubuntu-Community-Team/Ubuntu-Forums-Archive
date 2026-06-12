---
title: "how can i run .bin files"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by waqas_butt0071 on 2007-02-23
can any body tell me how can i run .bin files

---

### Post by igknighted on 2007-02-23
> **waqas_butt0071 said:**
> can any body tell me how can i run .bin files

/path/to/file.bin or, if you are already in the directory, ./file.bin.  Use sudo if you need root priveleges (ie, doing an install)

---

### Post by taurus on 2007-02-23
Or

```
chmod 755 **filename.bin**
./**filename.bin**
```

---

### Post by igknighted on 2007-02-23
Good call taurus.  The chmod command is needed to make the file executable.  An alternative to doing this would be to right click the file, click properties, go to the permissions tab and click the box labeled "make executable", if you prefer as little CLI as possible.

---

### Post by Maestro23 on 2007-02-23
Also:

> chmod +x filename.bin
./filename.bin

Just my 2 cents.:)

---

### Post by waqas_butt0071 on 2007-02-23
Thanks man

the file needed permissions to run and i have executed it thanks to u taurus, can u tell me where can i get the codes like 755 for giviing permissions using chmod,i mean to say that where can i get a list of these codes used for permission

---

### Post by Maestro23 on 2007-02-23
> **waqas_butt0071 said:**
> Thanks man

the file needed permissions to run and i have executed it thanks to u taurus, can u tell me where can i get the codes like 755 for giviing permissions using chmod,i mean to say that where can i get a list of these codes used for permission

File permissions: [http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)

---

### Post by danbopes on 2007-10-15
This thread is probably ancient, but it applys to me.

I downloaded a .bin file, threw it in my home directory, and tried running it.

chmod +x file.bin
./file.bin

But I keep getting:
bash: ./file.bin: No such file or directory

I tried chmodding it to 0755/0777, even tried running it as root, no luck.  Can any1 help?

---

### Post by steve.horsley on 2007-10-15
Bash seems to think your file is not there. Check you are typing the name in the correct upper/lower case. Did chmod give you an error?

Another possibility is that the .bin file is launching correctly, but then hte .bin file itself is trying to open a non-existent file.

---

### Post by wormser on 2007-10-15
The error is telling you that the file is not in that directory.  Make sure you are in the same directory as the file.bin when running those commands.

---

### Post by mali2297 on 2007-10-15
> **danbopes said:**
> This thread is probably ancient, but it applys to me.

I downloaded a .bin file, threw it in my home directory, and tried running it.

chmod +x file.bin
./file.bin

But I keep getting:
bash: ./file.bin: No such file or directory

I tried chmodding it to 0755/0777, even tried running it as root, no luck.  Can any1 help?

Here's one with the same error:
[http://ubuntuforums.org/showthread.php?p=3525260#post3525260](http://ubuntuforums.org/showthread.php?p=3525260#post3525260)

Do you have the 64-bit version of Ubuntu? If that is the case you might want to check the [X86 64-bit forum]("http://ubuntuforums.org/forumdisplay.php?f=134").

---

### Post by danbopes on 2007-10-15
Yeah, that was the problem...running ubuntu 64-bit.  Wish the errors were a bit more specific...but anyways, got it working.

---

### Post by mali2297 on 2007-10-15
> **danbopes said:**
> Yeah, that was the problem...running ubuntu 64-bit.  Wish the errors were a bit more specific...but anyways, got it working.

How? It might help others.

---

