---
title: "creating root"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by Draiocht on 2005-08-12
Hi all,

I am a newbie to ubuntu and indeed to linux as a whole. I like the look and feel of ubuntu but have run into one immediate problem. I chose default installation after downloading the ISO and burning a disk. Throughout the installation at no point was a root account created or a password for it set. Obviously I need to sign in as root to configure the system and administer it, but at the moment I can't. Can anyone tell me how to solve this problem?

---

### Post by varunus on 2005-08-12
Ubuntu/Kubuntu doesn't use the root account.  Instead, it uses something called "sudo".  This means that to become root in a terminal, type
```
sudo -s
``` 
and enter YOUR password.

Similarly, any actions that ask for a password, they need YOUR password.  This is more secure than having a root account, because a hacker doesn't know your username.

---

### Post by sophtpaw on 2005-08-12
[QUOTE=Draiocht]Hi all,

I am a newbie to ubuntu and indeed to linux as a whole. I like the look and feel of ubuntu but have run into one immediate problem. I chose default installation after downloading the ISO and burning a disk. Throughout the installation at no point was a root account created or a password for it set. Obviously I need to sign in as root to configure the system and administer it, but at the moment I can't. Can anyone tell me how to solve this problem?[/QUOTE]

I had the same concern when i first came over to Ubuntu from SuSE. But i've come to love Debian-style and Ubuntu's sudo, simpler you'll find. To find out more check wiki pages; for example:

[https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29)

Enjoy,

--
sophtpaw

---

