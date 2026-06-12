---
title: "Adding repositories?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-06-15
Is there any way to add universe and multiverse repositories from the command line?

---

### Post by Jagot on 2006-06-15
Well, you could edit the sources.list with nano or something:

```
sudo nano /etc/apt/sources.list
```

---

### Post by prash@linuxitarian on 2006-06-15
[QUOTE=meniscus]Is there any way to add universe and multiverse repositories from the command line?[/QUOTE]
if you don't want to use a text editor...

sudo -s
echo "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse" >> /etc/apt/sources.list

---

### Post by aysiu on 2006-06-15
prash@linuxitarian, I don't really know that much about using the echo command to insert lines into text files.

Would this command also do the same thing? ```
sudo echo "deb http://archive.ubuntu.com/ubuntu breezy universe multiverse" >> /etc/apt/sources.list
```

---

### Post by measure on 2006-06-15
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

then in sources.list

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free 
```

---

