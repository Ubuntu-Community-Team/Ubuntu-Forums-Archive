---
title: "[SOLVED] windows shares permissions"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-26
How do you change or assign permissions for access to window shares

Thanks

---

### Post by taurus on 2007-01-26
Share as in the same machine or over samba/network?

---

### Post by squrl on 2007-01-26
In another machine as in windows shares via the 192.168 address.

---

### Post by rmartz on 2007-01-26
First, Samba needs to be installed. You can install it several ways. Once installed, you need to go to Sytem>Administration>Shared Folders and tell it which folders you want to share and select "smb".

Each person will need an account on the Ubuntu machine to be able to access the shares. You can edit the smb.conf file to bypass this requirement.

---

