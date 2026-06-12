---
title: "Access Windows XP data from Ubuntu on dual boot system"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Le Hibou on 2006-09-28
I have installed Ubuntu onto the second (spare) disk of my WinXP home edition system. Then installed Opera as my default browser & e-mail client. All is looking good so far! However, in a dual-boot situation it would be simply wonderful if Opera (under Ubuntu) and Opera (under WinXP) could use the *same* data and configuration files. That way I don't have to transfer (or lose!) address lists, old e-mails, etc. Also, I would be able to receive e-mails into the same database (probably) whichever system I'm using at the time. (If Opera can work that way!). BTW, this is not really about Opera, there are lots of other files, documents, pictures, etc, & I don't want to do any kind of file transfer back and forth until I have decided, eventually, which system to keep! (I have no software any more which relies on Windows, so at the moment Ubuntu is favourite, if the data transfer issues can be solved).

If there is already a thread on this topic, could someone kindly point me to it? I'm sure it's a common problem, but I can't find any answers through the search...

---

### Post by Albi on 2006-09-28
sudo mount -t ntfs /dev/hda1 /windows -o nls=utf8,umask=0222

replace hda1 with the partition windows is in.  and try to search next time.  im assuming this is an ntfs partition as well

---

### Post by Kateikyoushi on 2006-09-28
I only shared my emails between the two OS, I did not trust about writing to ntfs so I made a fat32 partition and stored my mails there.

If you choose to try to write directly to your ntfs partition read [this]("http://ubuntuguide.org/wiki/Dapper#Windows").

---

### Post by Le Hibou on 2006-09-28
Thanks Albi, for the speedy response. It seems to work :D

---

### Post by Le Hibou on 2006-09-28
Sheesh, this forum moves fast!

Thanks, Kateikyoushi, that looks like a good source of information.

---

