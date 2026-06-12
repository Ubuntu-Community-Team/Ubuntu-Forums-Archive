---
title: "How do I reload the /etc/groups file once altered?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-08-13
Im adding users to various groups using the usermod command 

sudo usermod -a -G <group> <user>

This alters the /etc/group file (as planned).  How do I reload this information without having to log out or reboot the computer from the command line??

---

### Post by schorsch on 2007-08-13
```
id <user>
```

it should work immediately

---

### Post by bodhi.zazen on 2007-08-13
No, you have to log off and back on (you do not need to re-boot).

---

### Post by kevdog on 2007-08-13
Anything short of logging off and back on??

---

### Post by schorsch on 2007-08-13
If you are changing anything with another user, it will work at once:

```
 $ id gdm
uid=106(gdm) gid=111(gdm) groups=111(gdm)
$ sudo usermod -a -G lp gdm
$ id gdm
uid=106(gdm) gid=111(gdm) groups=111(gdm),[COLOR="Red"]7(lp)[/COLOR]
 
```

If you are changing your currently logged in user it can take a few moments:

```
 $ id schorsch
uid=1000(schorsch) gid=1000(schorsch) groups=1000(schorsch),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),85(usb),106(lpadmin),110(scanner),112(admin),1001(vboxusers)
schorsch@schorsch-linux:/etc/init.d$ sudo usermod -a -G lp schorsch
schorsch@schorsch-linux:/etc/init.d$ id schorsch
uid=1000(schorsch) gid=1000(schorsch) groups=1000(schorsch),4(adm),[COLOR="Red"]7(lp)[/COLOR],20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),85(usb),106(lpadmin),110(scanner),112(admin),1001(vboxusers)
 
```

... you do not have to reboot or logoff changing group permissions ...

---

