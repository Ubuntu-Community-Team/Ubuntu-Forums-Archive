---
title: "Location of shared windows files?"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by BitTorrentBuddha on 2006-02-01
Is there a specific location where I would find the files I've enabled sharing on on my windows box [yes, it's on the same network, I use the printer on it, Samba is installed, and I can access my shared ubuntu directories from my windows machine]

---

### Post by theturner on 2006-02-01
Take a look in Places > Network -> Windows Network (not sure whether that's the exact wording, my Ubuntu is set to German)

If nothing appears in there, type Alt+F2, and enter: smb://[IP_of_Windows_machine]
It should list all shares of the Windows box. If it doesn't, make sure you have smbclient installed.

---

### Post by BitTorrentBuddha on 2006-02-01
ahh, much obliged, running smb worked :)

---

