---
title: "Can't change permissions sda1"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Hairyred on 2006-07-30
The partition sda1 on my HD was NTFS, and I have formatted it to ext3 with Gnome Partition Editor. I can read from it as root  and user, but I can't write to it. I cannot change permissions because it says I am not the owner. I have tried sudo gedit/etc/fstab and have changed the ntfs entry to ext3 and  Sys>admin>disks shows it as ext3 and inaccessible. What do I do to change permissions to make this partition accessible to all users? The line in fstab is this: /dev/sda1 /media/sda1 ext3 ro,user,fmask=0111,dmask=0000 0 0
What do I change?
I have searched for an answer, but it's been days and I'm stuck!!

---

### Post by aysiu on 2006-07-30
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by Hairyred on 2006-07-30
THANKYOU!! All working!

---

