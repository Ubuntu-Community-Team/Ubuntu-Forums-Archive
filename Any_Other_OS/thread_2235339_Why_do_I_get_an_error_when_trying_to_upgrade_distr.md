---
title: "Why do I get an error when trying to upgrade distro on Kali linux?"
date: 2014-07-20
forum: Any Other OS
---

### Post by shahin on 2014-07-20
I hope I am in the right group; everything about Kali Linux seems to me to be a version of Ubuntu. If I am in the wrong group, please let me know. 


I am trying to upgrade a Kali Linux VM image to take advantage of Cuda technology, and I get the following error:

```

root@kali:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.14-kali1-amd64 (3.14.5-1kali2) ...
vmlinuz(/boot/vmlinuz-3.14-kali1-amd64
) points to /boot/vmlinuz-3.14-kali1-amd64
 (/boot/vmlinuz-3.14-kali1-amd64) -- doing nothing at /var/lib/dpkg/info/linux-image-3.14-kali1-amd64.postinst line 263, <STDIN> line 2.
initrd.img(/boot/initrd.img-3.14-kali1-amd64
) points to /boot/initrd.img-3.14-kali1-amd64
 (/boot/initrd.img-3.14-kali1-amd64) -- doing nothing at /var/lib/dpkg/info/linux-image-3.14-kali1-amd64.postinst line 263, <STDIN> line 2.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-3.14-kali1-amd64
/etc/kernel/postinst.d/zz-extlinux:
P: Checking for EXTLINUX directory... found.
/boot/vmlinuz-3.12-kali1-amd64
/boot/vmlinuz-3.14-kali1-amd64
P: Writing config for /boot/vmlinuz-3.14-kali1-amd64...
P: Writing config for /boot/vmlinuz-3.12-kali1-amd64...
I: os-proper disabled in /etc/default/extlinux: Skipping /boot/extlinux/os-proper.cfg
E: /usr/share/EXTLINUX/themes/debian: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.14-kali1-amd64.postinst line 591, <STDIN> line 2.
dpkg: error processing linux-image-3.14-kali1-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up extlinux (3:6.03~pre1+dfsg-1kali3) ...
P: Checking for EXTLINUX directory... found.
/boot/vmlinuz-3.12-kali1-amd64	/boot/vmlinuz-3.14-kali1-amd64
P: Writing config for /boot/vmlinuz-3.14-kali1-amd64...
P: Writing config for /boot/vmlinuz-3.12-kali1-amd64...
I: os-proper disabled in /etc/default/extlinux: Skipping /boot/extlinux/os-proper.cfg
E: /usr/share/EXTLINUX/themes/debian: No such file or directory
dpkg: error processing extlinux (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-amd64:
 linux-image-amd64 depends on linux-image-3.14-kali1-amd64; however:
  Package linux-image-3.14-kali1-amd64 is not configured yet.

dpkg: error processing linux-image-amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.14-kali1-amd64
 extlinux
 linux-image-amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I am follwing a tutorial here: [http://docs.kali.org/general-use/install-nvidia-drivers-on-kali-linux]("http://docs.kali.org/general-use/install-nvidia-drivers-on-kali-linux")

---

### Post by coffeecat on 2014-07-20
*Thread moved to **Other OS/Distro Support**.*

Kali is not a version of Ubuntu -  it is one of many distros that are based on Ubuntu. The first two main sections of the forum are for support for the official "flavours" of Ubuntu. 

[http://www.ubuntu.com/about/about-ubuntu/derivatives](http://www.ubuntu.com/about/about-ubuntu/derivatives)

I've moved this to the correct sub-forum for you.

---

### Post by shahin on 2014-07-20
Thanks

---

