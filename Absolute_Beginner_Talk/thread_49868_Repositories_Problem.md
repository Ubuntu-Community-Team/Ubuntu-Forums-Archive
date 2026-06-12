---
title: "Repositories Problem"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by Phixion on 2005-07-18
Hi there, I'm trying to add extra Repositories, I'm following the guide @ [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories) but I'm getting the following error when typing 'sudo cp /etc/apt/sources.list /etc/apt/sources/list_backup'

cp: cannot create regular file `/etc/apt/sources/list_backup': No such file or directory


Any help welcome.

Cheers

---

### Post by SGC on 2005-07-18
You have an extra slash between sources and list_backup, the copy command should look like this:
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

---

### Post by Phixion on 2005-07-18
[QUOTE=SGC]You have an extra slash between sources and list_backup, the copy command should look like this:
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup[/QUOTE]

buh i feel stupid now, thanks mate, i read it so many times to make sure it was right... its too early :)

---

