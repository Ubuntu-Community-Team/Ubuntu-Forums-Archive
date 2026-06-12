---
title: "Recovering Original Source List"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Pavilion on 2006-06-29
I did this at terminal: cd /etc/apt/ Then: ls And I discovered there is a back up source list in the apt directory: sources.list_backup_200606271311.  I don't know if this backup is created from Breezys' original source list when I allowed Automatix to change its source list.  However, I did the following: while in  /etc/apt/ directories.

[B] sudo cp /etc/apt/sources.list_backup_200606271311 /etc/apt/sources.list
[/B] I received no complaints?

Did I acheive anything by doing this?  Is there anyway to tell if Breezy has had its original source list restored?  I don't have a breezy live CD.   

Thanks in advance:smile:

---

### Post by kingmonkey on 2006-06-29
I think your probably ok - but can you post the contents of /etc/apt/sources.list just to make sure.

---

### Post by Pavilion on 2006-06-29
[QUOTE=kingmonkey]I think your probably ok - but can you post the contents of /etc/apt/sources.list just to make sure.[/QUOTE]

Hi Kingmonkey...

By the time I returned to the forum and read your post I had popped the Dapper Live CD into the machine and started its install.  Thanks for answering my post.  I'm the type that gets bored easily and I'm constantly putting Digital Research Dos [DR-Dos] to the various machines cleaning the hard drives so that I may try something different.  I know soon that I will intentionally recreate a similar situation, and, when I do, perhaps the question will be answered when I post the contents of /etc/apt/sources.list.

Thank you again:cool:

---

### Post by catlett on 2006-06-29
Just for your info, with that command you replaced the list that was in your /etc/apt/sources.list with the contents of the file /etc/apt/sources.list_backup_200606271311 (whatever that is). Bash is very powerful so be carefull with cp. Always make a backup because in this case you lost the contents of the original /etc/apt/sources.list. I'm a little worried about what will happen when you learn about rm :D

---

