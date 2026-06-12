---
title: "ftp access osx with ubuntu"
date: 2008-10-17
forum: Apple Hardware Users
---

### Post by second.exodous on 2008-10-17
I remember I couldn't get any shares to work in linux so from fire fox I would type something like [ftp://address_of_mac:macs_user_name:password](ftp://address_of_mac:macs_user_name:password) or something like that anyway.

Any idea what the correct line is?

---

### Post by tiresia on 2008-10-17
Have you enabled ftp share in MacOSX (System Preferences > Sharing > File Sharing)? Do you have Leopard or Tiger?

---

### Post by cyberdork33 on 2008-10-17
> **second.exodous said:**
> I remember I couldn't get any shares to work in linux so from fire fox I would type something like [ftp://address_of_mac:macs_user_name:password](ftp://address_of_mac:macs_user_name:password) or something like that anyway.

Any idea what the correct line is?
it should be something like [noparse]ftp://username:password@ipaddress[/noparse]. I would use an FTP client though rather than just Firefox...

---

### Post by sirhalos on 2008-10-17
Click Places then click Go to Server... select FTP then put the IP address in for Host your username and password. This will add your OS X machine to your Ubuntu desktop as a folder.

---

### Post by cyberdork33 on 2008-10-17
> **sirhalos said:**
> Click Places then click Go to Server... select FTP then put the IP address in for Host your username and password. This will add your OS X machine to your Ubuntu desktop as a folder.
yep that works too.

---

