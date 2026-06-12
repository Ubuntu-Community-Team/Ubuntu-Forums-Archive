---
title: "TRYING to install to install 7.10 on USB stick..."
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by nhague on 2008-02-23
heyhey!

I'm a Windows man through and through, but I've got a Linux itch that needs scratching... and I'm buggered if I know how to install this thing!!

OK - 

1.downloaded and successfully burnt 7.10 ISO.
2.booted OK into environment
3.followed TO THE LETTER (!) the pendrivelinux install to USB tutorial...
4.got to point (17) : "Type **cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubunto.ico casper/vmlinuz casper/initrd.gz /media/ubuntu710/** "  > THIS is where is fails - I get "no such folder" regarding the "/media/ubunto710" bit. (If this makes sense)

I hear all the time about the Linux community being really helpful, so I'm gonna try you all out :)

thanks in advance - Nathan Hague  +61 409 562637

---

### Post by bwhite82 on 2008-02-23
You need to create that directory before you can copy files to it and you need root priv to do so:

sudo mkdir /media/ubuntu710

You also need root priveleges to copy files to that directory as well.

-Cheers

---

### Post by dcstar on 2008-02-23
> **nhague said:**
> heyhey!

I'm a Windows man through and through, but I've got a Linux itch that needs scratching... and I'm buggered if I know how to install this thing!!

OK - 

1.downloaded and successfully burnt 7.10 ISO.
2.booted OK into environment
3.followed TO THE LETTER (!) the pendrivelinux install to USB tutorial...
4.got to point (17) : "Type **cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubunto.ico casper/vmlinuz casper/initrd.gz /media/ubuntu710/** "  > THIS is where is fails - I get "no such folder" regarding the "/media/ubunto710" bit. (If this makes sense)

I hear all the time about the Linux community being really helpful, so I'm gonna try you all out :)

thanks in advance - Nathan Hague  +61 409 562637

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by yellowbread on 2008-02-24
It sounds like the vfat partition on your USB stick is not mounted as /media/ubuntu710 when you issue the long cp command. What is the result of the terminal command
```
mount
```

---

