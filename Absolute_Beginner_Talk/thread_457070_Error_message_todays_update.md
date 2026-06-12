---
title: "Error message todays update"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-05-28
E: Problem parsing dependency Depends
E: Error occurred while processing thekompany-support (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


How do I correct this?:p

---

### Post by PriceChild on 2007-05-28
[http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

I suggest you find help on the getautomatix.com forums

---

### Post by starcraft.man on 2007-05-28
Or do as this person did [here.]("http://ubuntuforums.org/showthread.php?t=457010") Remove the file, and then purge automatix, then restore a working sources file from [ubuntuguide.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") If you want to continue to use automatix, then like pricechild said, ask them to fix the issue they caused >.>.

---

### Post by hakimaki on 2007-05-28
I had the same error.  Fixed it with a simple sudo apt-get update

---

### Post by rosswmcgee on 2007-05-28
Thank you the  sudo apt-get update did the trick. I run ubuntu Fiesty 7.04 on two computers. One is a clean install and no automatix, it did not have the problem. The other is an upgrade from Edgy and does have automatix. So I guess I am not a total creep, but Automatix did help me get started on Ubuntu. I had used Linspire and before that Lindows, so I am a Linux believer but far from Geek City.

---

### Post by arnieboy on 2007-05-28
> **rosswmcgee said:**
> E: Problem parsing dependency Depends
E: Error occurred while processing thekompany-support (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


How do I correct this?:p

The erring package has long been fixed and a simple

```
sudo apt-get update
```

will fix this issue

---

### Post by arnieboy on 2007-05-28
> **starcraft.man said:**
> Or do as this person did [here.]("http://ubuntuforums.org/showthread.php?t=457010") Remove the file, and then purge automatix, then restore a working sources file from [ubuntuguide.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") If you want to continue to use automatix, then like pricechild said, ask them to fix the issue they caused >.>.
More often than not you give very wrong solutions to most Automatix related support questions. If you really are so interested in answering Automatix related support questions, I would suggest you take a short crash course from the devs of Automatix about how it works. It would help both you and the users who you try to help solve Automatix related issues or to help them get rid of it completely.
We are available on #automatix on freenode

---

