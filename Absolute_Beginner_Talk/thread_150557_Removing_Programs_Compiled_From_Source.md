---
title: "Removing Programs Compiled From Source"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by dwessell on 2006-03-26
Hi all.. So if you compile a program from source.. Is deleting the installed files enough? Or is there more involved? Or does it matter on the program?

Thanks
David

---

### Post by garner_nc on 2006-03-26
Checkinstall is a handy utility for installing programs compiled from source. Instead of running make - install you run checkinstall. It will create a .deb package before installation to make removing the program easier.It will also create Slackware .tgz packages. Check out the web-site below.

[http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)

All the Best,
Doug White

---

### Post by taurus on 2006-03-26
If you install a program with "sudo make install," then you have to be in the same directory where you compiled and installed it and run this
```

sudo make uninstall

```

---

### Post by tr333 on 2006-04-07
[QUOTE=garner_nc]Checkinstall is a handy utility for installing programs compiled from source. Instead of running make - install you run checkinstall. It will create a .deb package before installation to make removing the program easier.It will also create Slackware .tgz packages. Check out the web-site below.

[http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)

All the Best,
Doug White[/QUOTE]
thanks for the info on this.

---

