---
title: "help! I broke my synaptic package manager"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Knoob on 2007-05-10
using synaptic, i was trying to reinstall anthy and then an error ocurred.

now when i open synaptic it issues this message

> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

and then it closes.

i can't use synaptic now.

how can i fix this?

---

### Post by alienexplorers on 2007-05-10
Please print out you sources list at /etc/apt/sources and post it here.

---

### Post by zvacet on 2007-05-10
```
sudo apt-get remove --purge file_name
```

Try to delete program that gives you trouble and see will it help.

---

### Post by Knoob on 2007-05-10
here is my sources.list

> 
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty universe

deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) feisty multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#added for japanese input (2007.04.23)
deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) feisty/


---

### Post by heimo on 2007-05-10
See if both of these files exist:
```
ls -l /var/lib/dpkg/status-old 
ls -l /var/lib/dpkg/status
```

---

### Post by Knoob on 2007-05-10
thanks for the quick response guys.

@zvacet, 
i tried this out, but still fails..
> sudo apt-get remove --purge anthy
Reading package lists... Error!
W: Encountered status field in a non-version description
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.



@heimo, 
yes there is a status-old file.
i copied it back to status
> sudo cp -a /var/lib/dpkg/status /var/lib/dpkg/status.bak
sudo cp -a /var/lib/dpkg/status-old /var/lib/dpkg/status

then opened synaptic but it still issues an error

i would appreciate more suggestions...

---

### Post by heimo on 2007-05-10
I'd open the status file in text editor and see if there's anything obviously wrong.

---

### Post by Knoob on 2007-05-10
@heimo
thanks for the tip.
the file was indeed messed up.

> in one line it had
Packag**u**: <blah>

instead of 
Packag**e**: <blah>

there were more of similar errors (different characters showing up)


how that happened, i have no idea.
i thought by using the GUI (Synaptic) i would avoid messing up the files.

anyway, i fixed it by manually editing the file. (the irony) 
update manager and synaptic are now working again!

thanks to all who helped out. your suggestions put me in the right direction.

---

### Post by heimo on 2007-05-10
Great you got it fixed. Next step... I saw someone with corrupted status file, because of faulty RAM memory. I'd suggest to run mem test - I think it's a choice in grub boot manager when you boot (if you don't see grub menu, you may need to hit ESC to get there). You probably need to run it for some time - couple hours at least to stress test memory.

---

