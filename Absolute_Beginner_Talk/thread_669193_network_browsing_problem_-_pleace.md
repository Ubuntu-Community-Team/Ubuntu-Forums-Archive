---
title: "network browsing problem - pleace"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by sloop on 2008-01-16
Hallo my friends.I have connection between ubuntu 7.10 PC and windowsXP PC.I use konqueror at the moment.But when I try to change file or make new one, it gives :access denied could not write to smb://<pc_name>. Is this problem of SMB protocol or there is other browser which hasn't this problm? Please friends I MUST to solv this.Thank you in advance.

---

### Post by self-defence on 2008-01-16
Hi,

I'm not sure but try it this way smb://username@hostname_or_ip/ if the user is guest use guest.

Best of luck

Bye

---

### Post by sloop on 2008-01-16
Doesn't work.I want to open text files with openoffice.Now I know that openoffice doesn't open directly from any browser, but I must do create new files and folders at least.This way can't do this unfortunately.

---

### Post by jd65pl on 2008-01-16
Have you added and enabled the samba user?

```

sudo smbpasswd -L -a [I]USER
[/I]sudo smbpasswd -L -e *USER*
```

You will then have to restart smb

```
sudo /etc/init.d/smb restart
```

---

