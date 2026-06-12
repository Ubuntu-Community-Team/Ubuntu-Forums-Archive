---
title: "Nautilus Connect to Server only SSH"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-09-05
When I go to Places > Connect to Server it only shows SHH or Custom Location. I have tried connecting to an FTP server and it says [ftp:///](ftp:///) is an invalid location, any packages I am missing? I installed ubuntu with the server installation and did a "sudo apt-get install gdm gnome-core" so I assume that I have something missing, thanks in advance.

---

### Post by p_quarles on 2007-09-05
You need to provide more details. What server are you trying to connect to with FTP? 

If the server belongs to you, you will need to install an FTP daemon before you can connect to it using the FTP protocol.

---

### Post by amrclutch1 on 2007-09-05
ftp.debian.org doesn't even work, something is wrong, i reinstalled nautilus, did a sudo apt-get autoremove nautilus --purge and sudo apt-get install nautilus, still not working, it only shows SSH in the list, no matter what FTP i connect to it says [ftp:///](ftp:///) is an invalid location.

---

### Post by p_quarles on 2007-09-05
Just a wild guess, but try this:
```
unset http_proxy
```

---

