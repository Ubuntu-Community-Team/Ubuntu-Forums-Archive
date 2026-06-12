---
title: "Import Mbox to evolution"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by IronArjen on 2006-08-15
I just switched from Windows XP, using Outlook mail client, to Ubuntu using Gnome and Evolution. Great because it looks really similar. Now I get some problems importing my old mail. I transferred my Outlook files using Mozilla.
THen when I click Import -> Forward I get a menu. Choice 1 Import settings and data from older programs -> Forward I get a message like No importable settigs found. When I check option 2 Single file I get a menu with two windows. The upper "filename" works, I can browse towards my file but the second "filetype" remains opaque and I cannot select Mbox (nor any other as a matter of fact). My guess permission issue

I went thru  the permissions and reset all that seemed important for me to RWX. My .evolution looks like this

drwxr-xr-x  9 arjen arjen  4096 2006-08-15 09:09 .
drwxr-xr-x 47 arjen arjen  4096 2006-08-15 09:16 ..
drwxr-xr-x  4 arjen arjen  4096 2006-08-14 16:21 addressbook
drwxr-xr-x  3 arjen arjen  4096 2006-05-18 12:00 cache
drwxr-xr-x  5 arjen arjen  4096 2006-05-18 12:00 calendar
-rw-------  1 arjen arjen     3 2006-08-15 09:09 camel-cert.db
-r--r--r--  1 arjen arjen 65536 2006-05-17 11:26 cert8.db
-r--r--r--  1 arjen arjen 16384 2006-05-17 11:26 key3.db
drwxr-xr-x  7 arjen arjen  4096 2006-08-15 09:09 mail
drwxr-xr-x  5 arjen arjen  4096 2006-08-14 16:20 memos
-r--r--r--  1 arjen arjen 16384 2006-04-26 18:48 secmod.db
drwxr-xr-x  2 arjen arjen  4096 2006-08-15 08:59 signatures
drwxr-xr-x  5 arjen arjen  4096 2006-05-18 12:00 tasks

All file within directories are also rwx.
Is there another setting that I should change?

---

