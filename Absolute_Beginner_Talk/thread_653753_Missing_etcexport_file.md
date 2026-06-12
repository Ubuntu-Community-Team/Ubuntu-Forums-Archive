---
title: "Missing etc/export file"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by markyoung1984 on 2007-12-30
I am trying to make my computer a NFS and I'm following instructions from [http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)   In section 3 the instructions mention a file called export in the etc folder.  However, I cannot find this file?  I am using an Ubuntu desktop version, do I need the server version?  If I do need the server version, then how do I upgrade to it from the desktop version????  I'm extremely new to Linux but its actually quite nice.

On a separate note, are there any viruses for Linux and if so, where can I get some anti-virus software?

I look forward to your replies.  Cheers!!!!

---

### Post by llamakc on 2007-12-30
The file's name is "exports" and it is in /etc:

/etc/exports

[https://help.ubuntu.com/community/SettingUpNFSHowTo#head-ac7dfba15ed58c9d4cdb3417a2ab2f2433d444f0](https://help.ubuntu.com/community/SettingUpNFSHowTo#head-ac7dfba15ed58c9d4cdb3417a2ab2f2433d444f0)

---

### Post by arvevans on 2007-12-30
arv@arv-desktop:~$ ls /etc/exports
/etc/exports
arv@arv-desktop:~$ cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
arv@arv-desktop:~$

---

### Post by markyoung1984 on 2007-12-30
I tried the link you sent llamakc but the sudo command I copied into terminal replied stating it couldn't find the portmap package.  I tried looking in Package Manager but portmap doesn't exist, any ideas?

---

### Post by craigvanaman on 2008-06-27
you need to install the NFS server package:

# sudo apt-get install nfs-kernel-server

this will create the /etc/exports file.

---

