---
title: "Help finalizing Ubuntu install on Wallstreet Powerbook"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by ScooterDMan on 2007-02-15
I have meticulously followed [these instructions]("http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/") for getting Ubuntu up and running on my Powerbook G3 Wallstreet.

Everything goes fine, until I get to the last part, where the author gives important instructions regarding copyin theLinux kernel and ramdisk image to the OS 9 partition. 

I hit alt f2 to get into the command line, but I get a # sign instead of a $ sign. I am not sure if this is a problem, but I ignored it, and typed out all the commands as instructed.

They are:

```
cd /target
mkdir hfs
mount /dev/hda8 hfs -t hfs
```

and then...
```

cp boot/vmlinux hfs/System\ Folder/Linux\ Kernels/vmlinux
cp boot/initrd.img hfs/System\ Folder/ramdisk.image.gz
```

What's puzzling to me, is that I don't seem to get any response that anything is happening after I hit enter. Upon reboot, as instructed, I choose Linux from BootX, but when it starts back up, it seems to be reinitializing the installation (it asks for language selection, which I have already completed.

Not sure what to do. Please help.

---

### Post by equal on 2007-02-16
Hi there. Wow that's a complicated issue you've got going on. I would like to make a suggestion. I get the impression that you're installing Breezy because it's an older version, and you've got an older computer. If that is the case, forget that logic. Breezy is only a year older, it has the same system requirements. If you're looking to lower the resource demands, I would suggest downloading Xubuntu. It's a much lighter window manager, which should allow you to breeze through use.

If you've got at least 128MB RAM, you can use the live installer cd here:
[http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.10/release/xubuntu-6.10-desktop-powerpc.iso]("http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.10/release/xubuntu-6.10-desktop-powerpc.iso")
If not, use this CD instead:
[http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-powerpc.iso]("http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-powerpc.iso")

Good luck!

---

### Post by ScooterDMan on 2007-02-16
Thanks. I run Xubuntu on some old iMacs, and I love it. Do you think I will be able to run the live CD on this old Wallstreet, given that it's an Old World Mac?

---

