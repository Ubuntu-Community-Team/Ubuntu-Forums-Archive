---
title: "chmod or chmod -R"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by editrix on 2005-10-12
Probably a really stupid question, but ...

I've seen instructions on this forum to use the -R switch. What's it do?

---

### Post by nitricacid on 2005-10-12
This is what it says -R does when you type ```
chmod --help
``` '-R, --recursive         change files and directories recursively'

---

### Post by editrix on 2005-10-12
Blush! Yeah, it was a really stupid question. But thanks for reminding me there *are* manuals--arcane though they may be.

---

### Post by wishyjr on 2005-10-12
well, i'll go one better and ask, what does 'chmod' actually do? silly question i know but i dont know so... :) thanks

---

### Post by nitricacid on 2005-10-12
Give a folder\file rites. Such as changeing a file\folder so that anyone can use it. 


atleast I think that is what chmod does (maybe I am thinking of chroot). If i am wrong i know someone will currect me.

---

### Post by SilentCacophony on 2005-10-12
You can use chmod to allow your user(s) or group(s) full or restricted access to a certain folder.

Caution should be used in doing so, of course, especially with the -R option. Don't ever attempt anything like *sudo chmod -R a+w /*, for example. Bad things can happen. ;)

If you're looking to increase permissions for a mounted partition, there are options for that which you can set in /etc/fstab.

Best to read the manuals if you don't understand permissions in linux, for example:

man chmod
man chown
man mount
man fstab

---

