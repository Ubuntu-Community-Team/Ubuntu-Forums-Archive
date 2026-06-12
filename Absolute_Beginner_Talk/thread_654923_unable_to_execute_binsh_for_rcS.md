---
title: "unable to execute /bin/sh for rcS:"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by donwoodsnet on 2007-12-31
It seems I've lost the /bin/sh symbolic link.
I was doing a custom kernel per [HOW TO ]("http://www.howtoforge.com/kernel_compilation_ubuntu")which told me to:
rm -f /bin/sh
ln -s /bin/bash /bin/sh

After the kernel modification my VMware server wouldn't initlize anymore using the new or old kernel.
So after that I removed the link and rebooted.. Crap now it's toast.

Message is as follows:
init: Unable to execute "bin/sh" for rcS: too many levels of symbolic links

I tried to use the CD to reset the shell but it doesn't work.
Is there a way to make it boot

---

### Post by nick_h on 2007-12-31
By default /bin/sh is a symbolic link to /bin/dash - to repair the system you will have to restore this with:
```
sudo rm /bin/sh
sudo ln -s /bin/dash /bin/sh
```

If you can't do this then you may have to boot with a Live CD and copy dash to sh.

---

### Post by dcstar on 2007-12-31
> **donwoodsnet said:**
> It seems I've lost the /bin/sh symbolic link.
I was doing a custom kernel per [HOW TO ]("http://www.howtoforge.com/kernel_compilation_ubuntu")which told me to:
rm -f /bin/sh
ln -s /bin/bash /bin/sh

After the kernel modification my VMware server wouldn't initlize anymore using the new or old kernel.
So after that I removed the link and rebooted.. Crap now it's toast.

Message is as follows:
init: Unable to execute "bin/sh" for rcS: too many levels of symbolic links

I tried to use the CD to reset the shell but it doesn't work.
Is there a way to make it boot

The standard "/bin/sh" is a link to "/bin/dash", you may want to restore it.

---

### Post by spiderbatdad on 2007-12-31
sudo ln -s bash sh

---

### Post by donwoodsnet on 2007-12-31
So far no luck...
The only way I can see the boot disk it to boot from a live rescue CD.
sudo doesn't work.
I don't have a backup tape
The disk is on /dev/sda1 and I can make it mount on target
cd /target/bin and I can see sh
None of the command that's been suggested works when I reboot

---

### Post by nick_h on 2007-12-31
Try:
```
cd /target/bin
rm sh
cp dash sh

```
and then reboot.

---

### Post by donwoodsnet on 2007-12-31
> **nick_h said:**
> Try:
```
cd /target/bin
rm sh
cp dash sh

```
and then reboot.

I did just that and it says unable to stat /target/bin/sh : input/output error.
I booted from the rescue cd and ran e2fsck on /dev/sda1 and it fixed the i/o problem with sh.
cp /target/bin/dash /target/bin/sh and now the system boots.
So now i'm back to why the vmware server won't boot after doing a kernel change how to from [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
Thanks for the help.

---

### Post by dcstar on 2007-12-31
> **donwoodsnet said:**
> 
...........
So now i'm back to why the vmware server won't boot after doing a kernel change how to from [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
Thanks for the help.

Well, wouldn't it be simpler just to boot a standard kernel and have a fully functional system?

---

### Post by donwoodsnet on 2007-12-31
> **dcstar said:**
> Well, wouldn't it be simpler just to boot a standard kernel and have a fully functional system?

The point was trying to get 8 gig of ram working with the system but that didn't seem to work either. 64bit here I come.

---

### Post by nick_h on 2008-01-01
You could try reading and posting in the [Master Kernel](http://ubuntuforums.org/showthread.php?t=311158) thread.

---

