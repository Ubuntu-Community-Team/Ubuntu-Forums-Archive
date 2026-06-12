---
title: "Why do I get this message when extracting a file?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by zakeen on 2007-11-27
I use archive manager and get this error for extracting the VMware tar.

```

tar: vmware-distrib/lib/vmware-vmci/lib/libvmci.so.0: Cannot create symlink to `libvmci.so.0.0.0': Operation not permitted
tar: vmware-distrib/lib/vmware-vmci/lib/libvmci.so: Cannot create symlink to `libvmci.so.0': Operation not permitted
tar: vmware-distrib/vmware-install.pl: Cannot create symlink to `bin/vmware-uninstall.pl': Operation not permitted
tar: Error exit delayed from previous errors

```

---

### Post by ukripper on 2007-11-27
> **zakeen said:**
> I use archive manager and get this error for extracting the VMware tar.

```

tar: vmware-distrib/lib/vmware-vmci/lib/libvmci.so.0: Cannot create symlink to `libvmci.so.0.0.0': Operation not permitted
tar: vmware-distrib/lib/vmware-vmci/lib/libvmci.so: Cannot create symlink to `libvmci.so.0': Operation not permitted
tar: vmware-distrib/vmware-install.pl: Cannot create symlink to `bin/vmware-uninstall.pl': Operation not permitted
tar: Error exit delayed from previous errors

```

If this file is meant to be under root permissions you won't be able to extract without being root or use command line using sudo. you can change permissions of this file through command line using either chmod or chown

---

### Post by toupeiro on 2007-11-27
> **ukripper said:**
> If this file is meant to be under root permissions you won't be able to extract without being root or use command line using sudo. you can change permissions of this file through command line using either chmod or chown

sudo file-roller

---

### Post by ukripper on 2007-11-27
> **toupeiro said:**
> sudo file-roller

?

---

### Post by zakeen on 2007-11-27
What is the command for archive manager?

---

### Post by ukripper on 2007-11-27
> **zakeen said:**
> What is the command for archive manager?
```

sudo tar jxvf file.tar.bz2
```


If it is tar.gz  then  **zxvf** in place of jxvf in the command line.

Full details available here [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

---

