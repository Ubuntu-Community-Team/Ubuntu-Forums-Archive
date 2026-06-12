---
title: "Samba No Password"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by boso on 2007-06-14
Hi,

I have a Media Player on my network which can only connect to Windows shares. I have set up Samba on my network, however, I can't connect to the shares, as the player does not allow you to enter a user name or password. 

Is there anyway to configure Samba to bypass the whole username and password thing? Thanks.

---

### Post by starcraft.man on 2007-06-14
> **boso said:**
> 
Is there anyway to configure Samba to bypass the whole username and password thing? Thanks.

Disable the password off the account your logging into in windows, samba doesn't ask me for any pass when I reach into my Win computers. There's probably another way but thats how I do it...

---

### Post by boso on 2007-06-14
The Media player needs to connect to the Ubuntu machine. 

I just need the player to connect to Samba without a username and password, as it does not have this capability.

---

### Post by mycroes on 2007-06-21
It's quite easy actually...

- Open up /etc/samba/smb.conf
- Set "security = share" (probably you'll find a security = user commented, just add the line under that one).
- set "guest account = smbuser" (at the commented line guest account = nobody).
- add the user smbuser (sudo useradd -g users smbuser)

Now it should work. Of course you should check that a share that you want access to doesn't have "guest ok = no" because that'll keep the guest account out. Another way to solve your issue (probably, not sure) would be to connect to a network share in windows. This will map the share to a drive letter, which should be accessible by any app...
Regards,

Michael

---

