---
title: "How do I log in as root to change the permissions on /media/disk?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by krazejpo on 2007-05-08
I'm using Ubuntu Feisty Fawn I want to access my 2nd hard drive but it says under permissions that the owner is root, so I need to change the owner to me (i guess). How do I do that? Please Help!!!!!!!

---

### Post by Bachstelze on 2007-05-08
Which filesystem is the partition formatted in ?

---

### Post by krazejpo on 2007-05-08
What do you mean?

---

### Post by Bachstelze on 2007-05-08
I mean what kind of partition is it ? FAT ? NTFS ? ext3 ?

---

### Post by krazejpo on 2007-05-08
Ntfs

---

### Post by Bachstelze on 2007-05-08
See here, then.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by krazejpo on 2007-05-08
Thanks I'll let you know if it worked thanks again

---

### Post by krazejpo on 2007-05-08
It didnt work, all I want to do is sign in as root so that I can change the permission on the /media/disk. /media/disk doesent contain windows.

---

### Post by Bachstelze on 2007-05-08
You cannot change the permissions on a NTFS partition once it's mounted. Not even root can. You need to set the permissions at mount-time.

---

### Post by jiminycricket on 2007-05-08
I'd also recommend ntfs-config from the universe repository. [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Sulli on 2007-05-08
Is this booting from a live disk or install on hdd?

if it is installed on the Hdd from my limited experiance you will need a program called 3g-ntfs

[www.ntfs-3g.org](www.ntfs-3g.org) 

However you should be able to install it via your synaptics package manager. Just search for ntfs should do the trick

---

### Post by krazejpo on 2007-05-08
I fixed the problem thanks to my friend Machinevirus, all I had to do is go to synaptic package manager, search for ntfs-config and install it. After that you look for it in Applications- System Tools- NTFS Configuration Tool and then enable write support for internal device. click ok. And now you can write and delete files on it! TRUST ME IT WORKS!!!! Create a folder in it and see for yourself!!!

---

