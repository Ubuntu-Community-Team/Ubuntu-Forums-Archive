---
title: "Cannot change power states of guest OSes in vmware server"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by eoghanmurray on 2007-06-15
I ran VMWARE Converter for Windows and wrote the files to an external hard disk, which I have full access to in Ubuntu 7.04. I can open the virtual machine perfectly, but when I press 'power on, I get this error:

```
Unable to change virtual machine power state: The process exited with an error:
vmxvmdb: Index name being generated from config file
POST(no connection): Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

POST(no connection): Failed to initialize monitor device.

Failed to initialize VM.
End of error message.
```

Ty in advance! ;)

---

### Post by Bachstelze on 2007-06-15
It seems vmware is not correctly configured for your system. Try to run :

```
sudo /usr/bin/vmware-config.pl
```

---

### Post by eoghanmurray on 2007-06-15
Returned:

```
sudo: /usr/bin/vmware-config.pl: command not found

```

---

### Post by eoghanmurray on 2007-06-15
vmware just crashed my laptop

---

### Post by Bachstelze on 2007-06-15
How did you install vmware ?

---

### Post by eoghanmurray on 2007-06-15
i use a .deb file from a canonical guide.

---

### Post by eoghanmurray on 2007-06-17
OK. Uninstalled VMWare Server and installed player: when I load a *.vmx file I get this error message:

```
Error while powering on: Failed to launch peer process.
```

Thx for any help in advance!

---

### Post by Bachstelze on 2007-06-17
You must spot the vmware-config.pl script and run it, it will configure vlware for your system (also, if you ask me, I prefer to install vmware with the tarballs from vmware.com than with DEBs).

---

### Post by eoghanmurray on 2007-06-17
What would you type in terminal to run vmware-config.pl?

---

### Post by Bachstelze on 2007-06-17
Just type it's path, for example if it's in /usr/bin, you type :

```
sudo /usr/bin/vmware-config.pl
```

---

### Post by chenel on 2007-06-23
I was able to fix this problem by installing a newer version of the vmware server kernel modules: I had vmware-server-kernel-modules-2.6.20-15 installed, and once I installed vmware-server-kernel-modules-2.6.20-16 (a different package for some reason), everything worked.

---

