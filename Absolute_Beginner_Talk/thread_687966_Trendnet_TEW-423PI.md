---
title: "Trendnet TEW-423PI"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Tristicus on 2008-02-04
I need to get this working somehow. I am not familiar with anything or how to install or use NDISWrapper or anything....I have been away from Linux for too long and decided to dual boot so I need some help!.

---

### Post by coolbrook on 2008-02-04
You can install ndiswrapper from the CD

```

sudo apt-get install ndiswrapper-common

```

I have the same card.  The wireless driver is in the link in my sig.  Extract it and then copy it from Windows to a folder in Ubuntu.

```

sudo ndiswrapper -i path/toyour/file**.inf**
ndiswrapper -l
```

should show that it's installed with a driver present.

```
sudo modprobe ndiswrapper
sudo depmod -a
sudo gedit /etc/network/interfaces
```

add *ndiswrapper* to a line at the bottom of the interfaces file, save close and reboot.  Then try to connect to your network.

---

### Post by Tristicus on 2008-02-04
Will try tomorrow, thanks!

---

### Post by cmdowns on 2008-06-17
Hello, I am having the same problem with the same wireless adapter. I would like to try to follow this advice:

> **coolbrook said:**
> 
I have the same card.  The wireless driver is in the link in my sig.  Extract it and then copy it from Windows to a folder in Ubuntu.


But unfortunately, I don't know how to use ftp. Could someone help me out here? I've installed gFTP, but I don't know how to use it. If some one could point me in the right direction, it would sure help.

Or, if there is another solution that doesn't require FTP, that would be fine too. My main interest is getting my wireless card working. The FTP thing is really just a means to an end.

Thanks in advance!

---

