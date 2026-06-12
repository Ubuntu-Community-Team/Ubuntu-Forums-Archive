---
title: "Question about Partitioning"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by meseleto on 2006-09-30
So I was telling my college roomate about how awesome ubuntu was and how much I loved it and he decided to download it. :-D  Problem is, he didn't know what partitioning was and choose to use all of his hardrive for ubuntu and erased windows xp. :(  Now he wants to know if there is anyway he can get back Windows Xp without the system restore disk. Any ideas?

---

### Post by tagra123 on 2006-09-30
Windows will need to be reinstalled if the partition was removed and written over. 

If hes going to reinstall windows whynot just install vmplayer or server and create a virtual machine within ubuntu. He can then have both operating systems and not have to dual boot.

---

### Post by bulldog on 2006-09-30
> **tagra123 said:**
> Windows will need to be reinstalled if the partition was removed and written over. 

If hes going to reinstall windows whynot just install vmplayer or server and create a virtual machine within ubuntu. He can then have both operating systems and not have to dual boot.

Exept when he wants to play a DirectX game,that won't work in VMware.

Install windows again and choose to make a partition which left room for Ubuntu.
About 20GB is enough to install Ubuntu.

Your hdd is definitly erased,so getting windows back is out of the question

---

### Post by Psychoduck on 2006-09-30
I have a question about installing Ubuntu on my PC.  I got the cd in the mail the other day, and would like to install it in a new partition on my hard drive.  I already have XP on it, and the primary partition is the entire drive space of 120 gigs.  How would I go about re-partitioning without deleting any of my Windows stuff so that I could boot to either XP or Ubuntu??

HELP!!

Duck

---

### Post by xpod on 2006-09-30
Defrag a couple of times while your waiting for a decent reply is a good start:D

---

### Post by bulldog on 2006-09-30
You can create a new partition by resizing your drive within windows or ubuntu,take the one you prefer.

Think carefully about the amount of space you want to have for your windows and your ubuntu as well.

Altering later could be done,but if you're make a slight mistake,it can cost you your data.

Before you start resizing run defrag several times.
Right click your My Computer and choose administration,and look for disk management.
Here you can create a new partition for ubuntu.

---

### Post by tagra123 on 2006-09-30
Following up on bulldog:

If you want to play games then dual booting is the answer.  If the only apps you use are for word processing, programming and the like then vmware works well.

If you have an 80GB drive I'd do something similar to this using gparted on the live cd.

20GB hda1 = windows (ntfs)
30GB hda2 = windowlinuxshare (fat filesystem)
10GB hda3 = / (linux root filesystem)ext3
10GB hda4 = /home (linux home folder)ext3
9GB  hda5 = backup partition (ext3 or fat)
hda6 = swap

Install windows on hdc1 "C:\" and then make a directory on hdc2 "D:\" called  "Mydocs" and then move your my documents using the windows wizard to the D:\Mydocs directory. By doing this you can have access to them easily from ubuntu.

After windows is installed and working then install ubuntu, but when it gets to the partition selection stage of the install use the manual option and choose the above partitions -- hda3 for the root, hda4 for home, etc, etc.

By the way the hda numbers may be different and usually will be because of primary and logical partions may assign another number. so it may be closer to hda1, hda3, hda4, hda6 etc...

The backup partition makes it easy to make backups using partimage / rsync or tar to avoid this kind of situation in the future.

---

