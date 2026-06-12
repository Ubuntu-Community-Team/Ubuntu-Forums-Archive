---
title: "flash install problem"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by LookTJ on 2006-08-16
Problem:

looktj@looktj:~$ sudo apt-get install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree
looktj@looktj:~$


How do i fix this? Sorry I'm a newbie

---

### Post by Jagot on 2006-08-16
flashplugin-nonfree is in the multiverse repository which is not enabled by default.  See either of these methods to enable it:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

Irrelevant to your actual question, but you may want to use aptitude instead of apt-get.  Read this to see why:

[http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)

---

### Post by LookTJ on 2006-08-16
> **Jagot said:**
> flashplugin-nonfree is in the multiverse repository which is not enabled by default.  See either of these methods to enable it:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

Irrelevant to your actual question, but you may want to use aptitude instead of apt-get.  Read this to see wyhy:

[http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)

thanks very much for those help topic and i will use aptitude

---

### Post by denday on 2006-08-17
thanks for those link. its help me out. ;)

---

