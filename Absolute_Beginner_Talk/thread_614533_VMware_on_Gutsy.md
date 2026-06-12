---
title: "VMware on Gutsy"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-11-16
i downloaded VMware-server-1.0.4-56528.i386.rpm
converted it into a deb with --scipts option via alien.

and installed the resulting vmware-server_1.0.4-56529_i386.deb

It showed no errors, it said that its installed successfully. but from where can i start vmware server to create virtual machines.

This might be of some help...
```

root@eagles-nest:/home/chevaliar# locate vmware-server
/home/chevaliar/vmware-server_1.0.4-56529_i386.deb
/usr/lib/vmware/share/icons/48x48/apps/vmware-server.png
/usr/sbin/vmware-serverd
/usr/share/doc/vmware-server
/usr/share/doc/vmware-server/changelog.Debian.gz
/usr/share/doc/vmware-server/copyright
/var/lib/dpkg/info/vmware-server.prerm
/var/lib/dpkg/info/vmware-server.postrm
/var/lib/dpkg/info/vmware-server.conffiles
/var/lib/dpkg/info/vmware-server.preinst
/var/lib/dpkg/info/vmware-server.list
/var/lib/dpkg/info/vmware-server.postinst
/var/lib/dpkg/info/vmware-server.shlibs
/var/lib/dpkg/info/vmware-server.md5sums

```

---

### Post by veloce on 2007-11-16
That's a really strange way of installing, but if it worked then running "vmware" at the command line should start the vmware console.

The better way of installing is to download the script based installer.

---

### Post by shoaibi on 2007-11-16
isn't there a nice and handy .bin installation file for vmware workstation, like i have for google earth and netbeans, and also is it all in all command line based version?

---

### Post by k.bratovanov on 2007-11-16
From where can be this script based installer downladed?

---

### Post by hyper_ch on 2007-11-16
shaoibi:

Server or Workstation?

---

### Post by kvizz on 2007-11-16
[http://download3.vmware.com/software/vmserver/VMware-server-1.0.4-56528.tar.gz](http://download3.vmware.com/software/vmserver/VMware-server-1.0.4-56528.tar.gz)

---

### Post by shoaibi on 2007-11-17
well i installed the server version and its working fine on my system. Loving it.....

SOLVED!

---

