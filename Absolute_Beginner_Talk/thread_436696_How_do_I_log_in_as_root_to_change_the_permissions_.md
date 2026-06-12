---
title: "How do I log in as root to change the permissions on /media/disk?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by krazejpo on 2007-05-08
How do I sign in as root to change the permissions on a 2nd hard drive (2nd hard drive doesnt contain windows) PLEASE HELP!!!!

---

### Post by jiminycricket on 2007-05-08
If it's ntfs, use ntfs-config

Otherwise, follow [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by jfinkels on 2007-05-08
Take a look here for more information on root and sudo [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by krazejpo on 2007-05-08
I fixed the problem thanks to my friend Machinevirus, all I had to do is go to synaptic package manager, search for ntfs-config and install it. After that you look for it in Applications- System Tools- NTFS Configuration Tool and then enable write support for internal device. click ok. And now you can write and delete files on it! TRUST ME IT WORKS!!!! Create a folder in it and see for yourself!!!

---

