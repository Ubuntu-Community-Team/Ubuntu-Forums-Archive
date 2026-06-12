---
title: "FTP &amp; SSH on Ubuntu Desktop"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by geezerone on 2007-02-03
Hi

I am toying with the idea of FTP'g to and from an Ubuntu Deskop box and a windows box using SSH. I haven't used SSH or run an FTP server before but basically want to be able to download more than upload from it when in a different location.

I have done some searches here but think I need a few pointers as to what to get etc. I do have a static IP but also have a DynDNS account for what it's worth.

TIA

:)

---

### Post by Bachstelze on 2007-02-03
```
sudo apt-get install openssh-server
```

Will install the SSH server, which you can use to connect with SFTP too. All FTP clients that I know of support it.

---

### Post by geezerone on 2007-02-03
Thanks for that! Does the SSH server need any configuration and start with login etc?

With SSH how do you go about getting free keys and using them on server/client (cerberus for instance)?

---

