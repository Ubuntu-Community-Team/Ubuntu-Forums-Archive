---
title: "Mounting and Network Setting(by a noob)"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Holy Knight on 2007-06-16
Hello, i am anew user of Ubuntu 7.04,i just want some quick guidelines to resolve the following problems:

1)My Hard Disk have four partition,Ubuntu managed to mount three of them but one (dev/sda6) is not mounted.Can anyone help in mounting this partition (Disk Format is FAT32).

2)I have a LAN connection.It is connected through a Domain.Although Ubuntu already managed to detect the IP and DomainNameSever but how will I register my Computer name (7-nzfpc1113),Username(Somebody)and password(will not tell) assigned by my Network Administrator to the domain (just like in Windows)?

Sorry if i double posted,i was getting confused searching and reading other people's post.:)

---

### Post by zvacet on 2007-06-16
[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")


```
pppoeconf
```

---

### Post by Holy Knight on 2007-06-17
Thanks,that solved my first problem.But about the second problem,will I find it in the webpage you have given me?

If possible,can anyone simplify the procedure for solving the second problem?pretty please!!!I really want to use Ubuntu full-time.

---

### Post by zvacet on 2007-06-17
[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_configure_broadband_connections]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_configure_broadband_connections")

---

### Post by Gimpy_Rob on 2007-06-17
hi, I'll jump in on this...

zvacet is linking to a site that deals with broadband connection details, but you said you have a domain?  Now, I'm not actualy sure what is availible to connect, but to start, is there more information you can provide to tell us what you are trying to connect to? your administrator might be able to provide this information. What services are you connecting to? what does the domain controller control? can you access the outside internet now?

More info please:p

---

### Post by Holy Knight on 2007-06-17
> **Gimpy_Rob said:**
> hi, I'll jump in on this...

zvacet is linking to a site that deals with broadband connection details, but you said you have a domain?  Now, I'm not actualy sure what is availible to connect, but to start, is there more information you can provide to tell us what you are trying to connect to? your administrator might be able to provide this information. What services are you connecting to? what does the domain controller control? can you access the outside internet now?

More info please:p

Let see now,my computer is connected through a Local Area Network provider.Their network settings is not on Workgroup but under a domain which is providing and controlling Internet access as well as file and folder sharings among other computers connected on the same network.They using a Windows Network software for their networking.

Is this enough?
Also i think they a using ISA server.
And oh yeah,my domain is a DYNAMIC DNS type

---

