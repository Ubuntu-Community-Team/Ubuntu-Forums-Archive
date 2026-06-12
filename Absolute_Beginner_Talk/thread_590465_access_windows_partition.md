---
title: "access windows partition"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by SniperX99 on 2007-10-24
i would like to access my windows partition.  i have performed the following steps:

sudo fdisk -l
sudo mkdir /media/C /media/D
/dev/sda1 media/ ntfs nls=utf8,umask=0222 0 0

i then get an "access denied" message
can someone please explain what i'm doing wrong?
thanks

---

### Post by overdrank on 2007-10-24
> **SniperX99 said:**
> i would like to access my windows partition.  i have performed the following steps:

sudo fdisk -l
sudo mkdir /media/C /media/D
/dev/sda1 media/ ntfs nls=utf8,umask=0222 0 0

i then get an "access denied" message
can someone please explain what i'm doing wrong?
thanks

Hi and maybe this thread will help
[http://ubuntuforums.org/showthread.php?p=3605129#post3605129](http://ubuntuforums.org/showthread.php?p=3605129#post3605129)
Good luck! :KS

---

### Post by JoseArmandoJeronymo on 2007-10-24
I'm not sure how this is being done now but some versions ago there was a useful pack of scripts which Automatix would install. One of them is "root-nautilus-here".

If you manage to install that one navigate to where you want to be in your windows partition, right-click and choose the script. Enter your root password and a new window of Nautilus will open with read/write privileges.

I hope this helps.

---

### Post by SniperX99 on 2007-10-24
neither of those tips really helped at all, im not really sure why i would be given a permission denied message if i am the administrator, can someone explain this?

---

### Post by overdrank on 2007-10-25
> **SniperX99 said:**
> neither of those tips really helped at all, im not really sure why i would be given a permission denied message if i am the administrator, can someone explain this?

Hi and I am by no means a expert in the mounting of partitions and drives, I don't think it is a permission problem. I believe it is the command is wrong. Maybe this link will help
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by SniperX99 on 2007-10-25
> **overdrank said:**
> Hi and I am by no means a expert in the mounting of partitions and drives, I don't think it is a permission problem. I believe it is the command is wrong. Maybe this link will help
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

ok, using the link you provided, i'm up to the step where i edit /etc/fstab, so do i add the drive i want to the list? if so, what is the UUID and other information i need to input?

---

### Post by SniperX99 on 2007-10-25
bump

---

### Post by SniperX99 on 2007-10-26
anyone?

---

### Post by Niniel on 2007-10-26
I know even less than the last guy, but I can tell you that 7.10 has NTFS support built in, read and write. Nothing to configure. Just access away. After I installed Gutsy, the partition was detected and is being automounted. No need for any user intervention whatsoever.

---

