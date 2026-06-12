---
title: "Problem Installing 6.06 Server on G3 tower"
date: 2006-09-15
forum: Apple PPC Users
---

### Post by Giturar on 2006-09-15
I recetly aquired an old G3 tower and decided to install Linux on it and use it as a webserver to test my web apps and what not.

I chose Ubuntu 6.06 Server, however, when I try to boot from the CD, I get the following error:

```
/pci@80000000/pci-bridge@d/mac-io@5/ata-3@20000/disk@0:2,yaboot.conf: Unknown or corrupt filesystem
Can't open config file
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot: _
```

If I press Enter I get the following error:

```
Please wait, loading kernel...
:2,/vmlinux: Unable to open file, Invalid device
boot: _
```

Thinking something went wrong during the burn process, I burned a second CD and tried again, however, I got the same answer.

I searched the forums for similar errors, but found very little, but I saw something about using the Alternate version, which I tried, but I still got the same error.

Any ideas what could be going on?

I wish I could give more details about the tower, but all I know is that it has a G3 cpu and a 9GB hdd.

Thanks a bunch!

---

### Post by ristosu on 2006-09-15
I assume this is a Blue and White G3.

I think the Open Firmware device path (/pci@8000...) is incorrect. You should try to go into OF (Cmd-Opt-O-F after chime) and find your HD and CD ('dir cd:2,\' and if you get yaboot.conf, then use 'devalias' to see where cd points; looking at 'printenv' gives you current boot-device, probably hd).

I have booted successfully both Kubuntu and Xubuntu 6.06.1 DT on a similar machine. When I get back home in a few days, I can give you more details about OF.

---

