---
title: "Remove compiled software?"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by shane.reid on 2006-04-04
I complied wine from scratch, now I installed the deb from dapper...  how do i remove the compiled software whcih resides in /usr/local

if I just remove the files in /usr/local/bin, that won't solve it...

---

### Post by hollywoodb on 2006-04-04
do you still have the source folder with the compiled source in it (everything up until "make install") ? if so, try "make uninstall"

if not, you could compile it in *exactly* the same way again, and then run "make uninstall" ... not sure if you need to "make install" before "make uninstall" but I don't believe you do.

If you don't compile it in *exactly* the same way you won't get the results you're looking for

also, you can use checkinstall/installwatch at compile/install time to keep track of this sort of thing

---

### Post by taurus on 2006-04-04
You need to be in the same directory that you built and intalled wine.  Now, instead of running "sudo make install" to install it, you now need to type
```

sudo make uninstall

```

---

### Post by YokoZar on 2006-04-04
Protip: in the future, if you want to compile Wine from scratch, you're better off building the package from scratch:

apt-get --build source wine
sudo dpkg -i wine*.deb

Of course, this doesn't work for Wine CVS.

---

