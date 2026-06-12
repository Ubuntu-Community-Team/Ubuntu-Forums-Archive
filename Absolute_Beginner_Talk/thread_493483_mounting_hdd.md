---
title: "mounting hdd"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by knotman on 2007-07-05
when i try to get in to my other hdd it tells me the drives cant be mounted by policy any help please

---

### Post by aeiah on 2007-07-05
what do you mean by *policy*? is that your username? if not, if that the only information it is giving you?

i see from another thread that you've just installed, so welcome to ubuntu ;) when installing there was an option to set all your hdd mounting points but its easily missed. how are you going about trying to mount the hdds? there are several ways

---

### Post by knotman on 2007-07-05
yes i want to mount the other hard drives but when i go to do it it tells me "cannot mount volume "error org.freedesktop.Hal.Device.permissionDeniedby policy"

oh and thank you for the welcome

---

### Post by aeiah on 2007-07-05
the best way to add partitions is by editing the fstab directly. first you'll have to tell me some details about your partitions and which you want to mount. the clearest way is for you to do this:

go to your applications>accessories>terminal, and in there type:

```
sudo blkid
```

and enter your password. this will list the available partitions / drives. copy and paste the results here

---

### Post by Jem00 on 2007-07-05
R u dual-booting with windows?
Is your other hdd in ntfs format?

---

### Post by knotman on 2007-07-05
nothing is comming up i did see the other hdd when the program was installing but when i had to reboot they went away so now there is nothing on the desk top 
what im am tring to do is get access to the other two drives on the puter i install ubuntu on disk 2 i got win xp on disk 1 and disk three is storage ( i`m only trying to get to disk 3)

---

### Post by knotman on 2007-07-05
> **Jem00 said:**
> R u dual-booting with windows?
Is your other hdd in ntfs format?

yes all three hdds are nfts and i got win xp one disk 1 this ubuntu is on disk 2

---

### Post by knotman on 2007-07-05
i should metion that when i rebooted i choose option then booted i`m going to reboot and see what it said

---

### Post by knotman on 2007-07-05
when i rebooted i used my nickname and signed on (knotman (the first time )) when i rebooted this time i used my real name scott and the updates poped up i ddl clicked on the third hdd used the password and got right in nope problem now

---

