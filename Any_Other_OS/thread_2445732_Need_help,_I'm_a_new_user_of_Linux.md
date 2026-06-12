---
title: "Need help, I'm a new user of Linux"
date: 2020-06-18
forum: Any Other OS
---

### Post by outlawtrader on 2020-06-18
II have an acer c720 chromebook. I have fully wiped off Chrome os and reinstalled GalliumOS 3.1 via iso on a USB drive. I updated my packages and it says everything is up to date but I need to figure out what this error is or whatever is going on but i'm going to post it below 


W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:54
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:53
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:53
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:53
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:53
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:53
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list:54
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:53
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:53
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:53
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:53
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:53

I'm wondering how to fix this please and thanks

---

### Post by howefield on 2020-06-18
Thread moved to the "*Any Other OS*" forum.

---

### Post by outlawtrader on 2020-06-19
I'm sorry for the posting in a wrong thread I'm just new to the forum

---

### Post by SeijiSensei on 2020-06-19
You have multiple identical entries in /etc/apt/sources.list.  Just remove the duplicates.  The error message even tells you the offending line numbers.  Looks like removing lines 53 and 54 should do the trick.  After you make the edits run "sudo apt update" to see if the problem has been resolved. Make a backup of the sources.list file first just in case.

---

### Post by outlawtrader on 2020-06-20
Okay thank you. now as I have previously said I am new to linux, do i edit this like a text document ??

---

### Post by SeijiSensei on 2020-06-20
This file can only be edited by the "root," or administrative, user.  In Ubuntu, that means using sudo to run a command.  Open a terminal, then type
```

sudo nano /etc/apt/sources.list

```
You'll be prompted to enter your password. Nano has a useful menu of commands at the bottom of the screen.

---

### Post by oldrocker99 on 2020-06-21
And you just might like nano, as well. I certainly do.

---

