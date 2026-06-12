---
title: "Firefox upgrade"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Charlatat on 2006-05-08
Just wondering if there was a (easy and/or automatic!?) way to transfer bookmarks,settings,cookies etc. when FireFox is upgraded...

---

### Post by johnc4510 on 2006-05-08
The easiest way is to save your current bookmarks to a file in your home directory. Then after upgrade, import them back in.

---

### Post by aysiu on 2006-05-08
You won't have to transfer them. They'll work in the upgraded version.

If you want to be safe, you can make a backup of them, though. Just paste this command into a terminal: ```
cp -R ~/.mozilla ~/.mozilla_backup
```

You can upgrade to 1.5 right now using [this script](http://www.psychocats.net/ubuntu/firefox).

---

### Post by Seq on 2006-05-08
I'd reccommend using something like the foxmarks extension. I've grown quite fond of it (especially as you can use it to sync bookmarks on multiple machines).

I'm unsure what version of firefox you are upgrading from regarding foxmarks compatability. Regardless, this time it is probably easier to backup/restore your bookmarks.html as the previous poster suggest.

**Edit**: As aysiu points out, everything will just work. I'm just jaded from old mozilla suite releases when your bookmarks would be wiped... :p

---

