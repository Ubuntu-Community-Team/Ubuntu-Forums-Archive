---
title: "Whats wrong with my root user?!"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Eezyville on 2007-09-08
OK so I have two hdd on my laptop, I auto mount the one thats empty but my regular user cannot make files on it. So I had to give myself permission. I tired this: 
[PHP]  sudo chown -R USERNAME:USERNAME /media/mynewdrive[/PHP]

Didn't work. So I logged out and went in as the root user. I tried to manually add myself in and it said I didn't have permission as root??:confused:

wtf?!:confused:

---

### Post by aysiu on 2007-09-08
Is the drive FAT32 or NTFS? If so, you can't *chown*  it. You have to just change the mount options:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Eezyville on 2007-09-08
It is fat32, I'll look at that link you gave me. Thanks.:)

---

