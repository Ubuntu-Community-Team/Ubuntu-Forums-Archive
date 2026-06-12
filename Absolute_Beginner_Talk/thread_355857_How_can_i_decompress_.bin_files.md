---
title: "How can i decompress .bin files ?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by PoPPeRoNe on 2007-02-07
Hi,

I connected via SSH on my Root Server, i have the .bin file tranferred over FTP now i give the file permissions (chmod 777 *name of the bin file*.bin).

Now i will decompress the file with the followed command: /home/example/test.bin
but always i get the message " No such file or directory"

So what i do wrong ???

Please help me !!! :-/

Yours sincerely
PoPPeRoNe

---

### Post by taurus on 2007-02-07
```
cd /home/example
./test.bin
-or-
./home/example/test.bin
```

---

### Post by PoPPeRoNe on 2007-02-07
i have this do

```
xxxx:/home/Server#
xxxx:/home/Server# cd /home/Server/
xxxx:/home/Server# ./hldsupdatetool.bin
-bash: ./hldsupdatetool.bin: No such file or directory
```

---

### Post by taurus on 2007-02-07
Do you see that file on this list here?

```
ls -la
```

You need to be in the same directory where that file is.

---

### Post by PoPPeRoNe on 2007-02-07
```
XXXX:/home/Server# ls -la
total 3480
drwxrwxrwx 5 root    root       4096 2007-02-08 00:20 .
drwxr-xr-x 6   65003 ftpuser    4096 2007-02-07 22:02 ..
-rwxrwxrwx 1 cola    users   3513408 2005-09-02 04:27 hldsupdatetool.bin
drwxrwxrwx 2 root    root       4096 2007-02-07 23:43 Publik
XXXX:/home/Server#
```

The file is in the /home/Server/ folder ....

---

### Post by taurus on 2007-02-07
```
file hldsupdatetool.bin
```

---

### Post by PoPPeRoNe on 2007-02-07
```
XXXX:/home/Server# file hldsupdatetool.bin
hldsupdatetool.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped 
```

---

### Post by taurus on 2007-02-07
And you can't run it from there!

```
./hldsupdatetool.bin
-or-
sudo ./hldsupdatetool.bin
```

---

### Post by PoPPeRoNe on 2007-02-07
no i can´t run the file :(

```
XXXX:/home/Server# ./hldsupdatetool.bin
-bash: ./hldsupdatetool.bin: No such file or directory

XXXX:/home/Server# sudo ./hldsupdatetool.bin
sudo: unable to execute ./hldsupdatetool.bin: No such file or directory

```

---

### Post by confused57 on 2007-02-07
Here's mostwanted's instructions for using a .bin installer:
[http://www.monkeyblog.org/ubuntu/installing/#installer](http://www.monkeyblog.org/ubuntu/installing/#installer)

---

