---
title: "saving on a read-only disk"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by bellzii on 2008-04-16
i was writing a document and wanted to save it on my windows drive, it said 
You are trying to save the file on a read-only disk

---

### Post by forestpixie on 2008-04-16
Probably need to install ntfs config and ntfs 3g - what buntu are you using

sudo apt-get install ntfs-config ntfs-3g

will install a tool that you can use to get read/write on ntfs drives - you'll need to reboot

---

### Post by bellzii on 2008-04-16
im using ubuntu 6.10 Edgy, i know its pretty old, but ive had it about a year now

---

### Post by forestpixie on 2008-04-16
well I know that those 2 files worked for feisty but about edgy and them I know not - guess if you can install them they'll be ok.

---

### Post by mozetti on 2008-04-16
> **bellzii said:**
> im using ubuntu 6.10 Edgy, i know its pretty old, but ive had it about a year now

IIRC, I don't think Ubuntu used the ntfs-3g write capability in Edgy. Without setting it up manually, you won't be able to write to an NTFS-formatted drive.

---

