---
title: "edgy upgrade wont boot, HELP!"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by legolas on 2006-12-01
Hey I just tried to upgrade and now my 686 kernel won't boot.  It says:
cat: /etc/mdadm/mdadm.conf: no such file or directory.  I look into it and mdadm.conf has something to do with raid.  I have ubuntu on a sata disk, but the funny thing is, is that it boots fine with my old 386 kernel but not the 686.  Any suggestions would be greatly appreciated.
Also, can i use my old backups of / from dapper and install them on to edgy, or will that just mess her up?
Thank you

---

### Post by bodhi.zazen on 2006-12-01
> **legolas said:**
> Hey I just tried to upgrade and now my 686 kernel won't boot.  It says:
cat: /etc/mdadm/mdadm.conf: no such file or directory.  I look into it and mdadm.conf has something to do with raid.  I have ubuntu on a sata disk, but the funny thing is, is that it boots fine with my old 386 kernel but not the 686.  Any suggestions would be greatly appreciated.
Also, can i use my old backups of / from dapper and install them on to edgy, or will that just mess her up?
Thank you

Not sure if it will help, but perhaps boot to your 386 kernel and re-install the 686 kernel and mdadm ....

---

### Post by legolas on 2006-12-01
Nope. That did not do it.  Thanks for the try.  Anything else I might do?  I am really at a loss.

---

### Post by mushroom on 2006-12-01
edgy did away with the many different kernel options, so install linux-generic, and it should work. your 686 kernel is probably left over from the dapper install, and is probably versions behind the current one.

---

