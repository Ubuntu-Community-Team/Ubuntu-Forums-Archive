---
title: "Samb conf (screwed up)"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by majkmil on 2005-09-16
I ws trying to configure smba for file sharing. I used this command (sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo gedit /etc/samba/smb.conf) Then I changed some wording in the samb config file that I found on the starter guide and after I saved and restarted samba I got an error ( badly formed line) I think I am screwed. Was the original file save? Where would it be if it was?   Thanks for any help

---

### Post by aysiu on 2005-09-17
Just do the reverse: ```
sudo cp /etc/samba/smb.conf_backup /etc/samba/smb.conf
```

---

