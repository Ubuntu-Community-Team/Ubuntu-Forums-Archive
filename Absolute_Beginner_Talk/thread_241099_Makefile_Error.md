---
title: "Makefile Error"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Th3Futur3 on 2006-08-21
This is what happens in the terminal

  /bin/sh ../libtool --mode=install /usr/bin/install -c 'gpredict' '/usr/local/bin/gpredict'
/usr/bin/install -c gpredict /usr/local/bin/gpredict
/usr/bin/install: cannot remove `/usr/local/bin/gpredict': Permission denied
make[3]: *** [install-binPROGRAMS] Error 1
make[3]: Leaving directory `/home/alex/Desktop/src'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/alex/Desktop/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/alex/Desktop/src'
make: *** [install-recursive] Error 1

What should I do? Change the directory?

Also this happens.

alex@alex-linux:~/Desktop$ gpredict-0.5.99.7/INSTALL
bash: gpredict-0.5.99.7/INSTALL: Permission denied

---

### Post by taurus on 2006-08-21
Try to run it as root with the sudo command...

```
sudo gpredict-0.5.99.7/INSTALL
```

---

### Post by Th3Futur3 on 2006-08-21
alex@alex-linux:~/Desktop$ sudo gpredict-0.5.99.7/INSTALL
sudo: gpredict-0.5.99.7/INSTALL: command not found

Then I tried without sudo

alex@alex-linux:~/Desktop$ gpredict-0.5.99.7/INSTALL
bash: gpredict-0.5.99.7/INSTALL: Permission denied

---

### Post by Brownedwg89 on 2006-08-21
try
```
sudo sh gpredict-0.5.99.7/INSTALL
```

---

### Post by Th3Futur3 on 2006-08-21
This is what happend after I ran configure then I put in the code you gave me.

alex@alex-linux:~/Desktop$ sudo sh gpredict-0.5.99.7/INSTALL
gpredict-0.5.99.7/INSTALL: line 1: Installation: command not found
gpredict-0.5.99.7/INSTALL: line 2: config.h: command not found
gpredict-0.5.99.7/INSTALL: line 4: syntax error near unexpected token `C'
gpredict-0.5.99.7/INSTALL: line 4: `Copyright (C) 1994, 1995, 1996, 1999, 2000, 2001, 2002, 2004, 2005 Free'

---

### Post by Th3Futur3 on 2006-08-21
Any other suggestions?

---

### Post by Th3Futur3 on 2006-08-21
Well I thought I would let you guys know that I tried another source program to install and it will not let me Makefile. Says permission denied.

---

### Post by Th3Futur3 on 2006-08-22
bump

---

