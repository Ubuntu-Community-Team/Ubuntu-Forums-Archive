---
title: "so what's this &quot;Squashfs&quot; error ?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by DaveElson on 2007-06-11
Okay, I downloaded and burnt to disc, booted and ubuntu came up with options to start/install etc.
On trying to do so, I'm getting nothing but error messages and mainly "squashfs" errors.
Then it just goes to the cursor.

My system is AMD Athlon 1.3
I have windows already installed. Bios is from 2001.
Soory that I can't be more specific, it appears that there were over 200 of these errors.
Any help appreciated.

Edit: Although I did a search before posting, I must have done something wrong as nothing came up.
Just searched the forum again and it appears I may have to reburn the image at a slower speed. I'll try that tomorrow - off to bed now.
Any advice appreciated.

---

### Post by HackingYodel on 2007-06-11
Hi DaveElson,

**Squash**fs is a compressed, or squashed if you like, read-only file system.  Ubuntu uses it so that they can pack all that great software on to just one disk.

It sounds like your disk was corrupted somewhere along the way.  Follow the instructions here [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) to verify your image before you burn it to disk.  It's possible that a packet was jumbled during the download and is causing all your problems.

Good luck.

---

