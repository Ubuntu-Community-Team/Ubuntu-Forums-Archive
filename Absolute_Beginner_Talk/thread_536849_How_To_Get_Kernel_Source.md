---
title: "How To Get Kernel Source ?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Srikanth Krishnakar on 2007-08-28
[B][COLOR="Sienna"]Hi all,
I am newbie to UBUNTU, i have installed UBUNTU-7.0.4 in my machine, i am trying to get Source CODE for the driver of touchscreen, that is currently working, I donno how to proceed further . Ultimately i want the source of the kernel and Source code of the driver that is being used by ubuntu. I am awaiting for the replies urgently.  

Thanks & Regards
[COLOR="Navy"]**Srikanth Krishnakar**[/COLOR]
[/COLOR][/B]

---

### Post by asmoore82 on 2007-08-28
[ftp://ftp.kernel.org/pub/linux/kernel/v2.6/](ftp://ftp.kernel.org/pub/linux/kernel/v2.6/)

---

### Post by mysticmatrix on 2007-08-28
You can use apt-get to get source of any program in repositories
The command would be

```
sudo apt-get source <package-name>
```

---

### Post by Marat Galiev on 2007-08-28
go to packages.ubuntu.com
and install linux-headers,linux-source packages for you kernel.
Get you kernel version with command uname -r.

---

### Post by az on 2007-08-28
> **asmoore82 said:**
> [ftp://ftp.kernel.org/pub/linux/kernel/v2.6/](ftp://ftp.kernel.org/pub/linux/kernel/v2.6/)

No. Do not use upstream source.  Use the Ubuntu packages.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Marat Galiev on 2007-08-28
use packages from [http://packages.ubuntu.com.]("http://packages.ubuntu.com.i")
I posted right link here.

---

