---
title: "Permissions"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by realizee on 2008-02-17
Hi, i have a memorycard for my cellphone and when i try to send files to it, it just keep saying: "This is just a read-only disk." so please help , i don't know if it's the permissions but when i watched them i stood that i was the owner.

---

### Post by PmDematagoda on 2008-02-17
Post the outputs of:-
```
sudo fdisk -l
```
and
```
cat /etc/mtab
```

---

### Post by realizee on 2008-02-17
it doesn't work... :P

---

### Post by PmDematagoda on 2008-02-17
What do you mean it does not work?

---

### Post by realizee on 2008-02-17
and one more thing i have a bluetooth adapter could i use that for sending files to my cellphone?

---

### Post by realizee on 2008-02-17
I did those commands on the terminal, but i can't still send files to my memorycard... :P

---

### Post by PmDematagoda on 2008-02-17
> **realizee said:**
> and one more thing i have a bluetooth adapter could i use that for sending files to my cellphone?

You can using the appropriate applications.

---

### Post by PmDematagoda on 2008-02-17
> **realizee said:**
> I did those commands on the terminal, but i can't still send files to my memorycard... :P

Of course you can't, I need information before suggesting the solution, that is why I asked you to post the outputs you received from executing the commands.

---

### Post by meindian523 on 2008-02-17
> **realizee said:**
> I did those commands on the terminal, but i can't still send files to my memorycard... :P
realizee:
PMD means that you do those commands and post the outputs here.Those are not any commands which "enable" you to send files to your cellphone!

---

### Post by realizee on 2008-02-17
nima@code-desktop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b913c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14405   115708131   83  Linux
/dev/sda2           14406       14593     1510110    5  Extended
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/sdd: 252 MB, 252968960 bytes
8 heads, 61 sectors/track, 1012 cylinders
Units = cylinders of 488 * 512 = 249856 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
nima@code-desktop:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sdd /media/realize vfat ro,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
nima@code-desktop:~$ 



and what do u mean with appropriate applications, any suggestions?

---

### Post by meindian523 on 2008-02-17
Also,those appropriate apps are bluez-utils ,bluez-pin and gnome-bluetooth

---

### Post by PmDematagoda on 2008-02-17
> **realizee said:**
> nima@code-desktop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b913c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14405   115708131   83  Linux
/dev/sda2           14406       14593     1510110    5  Extended
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/sdd: 252 MB, 252968960 bytes
8 heads, 61 sectors/track, 1012 cylinders
Units = cylinders of 488 * 512 = 249856 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
nima@code-desktop:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sdd /media/realize vfat ro,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
nima@code-desktop:~$ 



and what do u mean with appropriate applications, any suggestions?

Do this:-

1) Unmount the memory card using:-
```
sudo umount /media/realize
```

2) Create a new directory in /media called force(just an example) using:-
```
sudo mkdir /media/force
```

3) Mount the memory card on the new directory using:-
```
sudo mount -t vfat /dev/sdd1 /media/force -o rw uid=1000
```

Then navigate to the /media/force directory and see if you can write to the memory card.

---

### Post by PmDematagoda on 2008-02-17
> **meindian523 said:**
> Also,those appropriate apps are bluez-utils ,bluez-pin and gnome-bluetooth

Those packages are the base, you would also need the gnome-vfs-obexftp package and start the service using:-
```
gnome-obex-server
```

---

### Post by meindian523 on 2008-02-17
Thanks,PMD.

---

