---
title: "rythmbox troubles + novell"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by pindus on 2006-08-26
Hi everyone.
I have some trouble with my rythmbox program.
The only station playable is the Virgin channel. I tried to install the gstreamer - plugin, but that didnt help. The other stations just wont play =(

And another one. I'm trying to connect to my novell-discs w/o success. Is there a special protocol for linux to connect with (like afp for mac)?

Thanx
Linda

---

### Post by pindus on 2006-08-26
I've now gotten this far

```
sudo mount //ipadress /network/ -o username=un,password=psw
```

but i get this error message
```
mount: wrong fs type, bad option, bad superblock on //ip-adress,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

syslog:
smbfs: mount_data version 1919251317 is not supported

```

Its a SAN-disc... shouldnt this work?

---

