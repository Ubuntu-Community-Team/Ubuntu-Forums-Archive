---
title: "A few questions"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by davidY on 2006-09-10
Hi,

I have just a few annoying problems:
1. I think I stuffed my sources.lst or whatever the package file is. can I revert this file?
2. I added some network entities that did not connect, so now an icon is on my network folder, but i cant delete it
3. How do I connect to somethinig that looks like : (for Mac) smb://id@domain.com/home/id or something like (for windows) \\files\home\id with user name as GROUP1/id

---

### Post by wieman01 on 2006-09-10
**_As to question number 1:_** You can update your source.list manually. Either generate the list of repository links yourself using...

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

Or use this (although I recommend to create a list on your own):

> # Ubuntu 'Main' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

# Ubuntu 'Universe' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

# Ubuntu 'Backports' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Ubuntu Bug Fix Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

# Ubuntu Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

---

### Post by xyz on 2006-09-10
Did you make a backup of your sources.list?

Otherwise, I guess, you could ask someone who uses the same Ubuntu version to mail you his/her sources.list!!!!...and then adjust it to your specific needs!

---

