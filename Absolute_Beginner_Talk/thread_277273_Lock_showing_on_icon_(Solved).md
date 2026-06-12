---
title: "Lock showing on icon (Solved)"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-10-14
Why is there a little lock at the top right corner of a couple of my icons on my desktop? I moved a couple of jpg files from windows to my desktop and the little locks appeared.

---

### Post by PriceChild on 2006-10-14
Seems like permissions have been incorrectly set when you move from a write protected ntfs drive.

do a
```
sudo chmod 775 -R ~/Desktop
```to sort it all out :)

---

### Post by HareBall on 2006-10-14
> **PriceChild said:**
> Seems like permissions have been incorrectly set when you move from a write protected ntfs drive.

do a
```
sudo chmod 775 -R ~/Desktop
```to sort it all out :)

Thanx

---

