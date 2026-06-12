---
title: "odd permissions"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-06-11
I have odd permissions on files. Some I cannot delete, eg on my desktop, some I cannot execute. Question. How can I reset ALL permissions to how they should be with me <tony> as root with supercow powers?

Tony

---

### Post by 67GTA on 2007-06-11
sudo chown -R system_username /location_of_files_or_folders

---

### Post by lazyart on 2007-06-11
As for making a file executable, you can go to the properties of the file and set it that way, or by command line:```
cmod +x *filename*
```If that gives a permission problem, do it with sudo.

---

### Post by tchoklat on 2007-06-11
tony@tony-desktop:~$ sudo chown -R tony /home
sudo: must be setuid root

thought please?

---

### Post by 67GTA on 2007-06-11
Try becoming root first. Type "su" hit enter and then your root password.

---

### Post by tchoklat on 2007-06-11
tony@tony-desktop:~$ su
Password: 
su: Authentication failure
Sorry.


odd eh!

---

### Post by 67GTA on 2007-06-11
You will have to set your root password. Type "sudo passwd" in a terminal and type what you want your root password to be.

---

### Post by tchoklat on 2007-06-11
thanks for your persistance, though now I get

tony@tony-desktop:~$ sudo passwd
sudo: must be setuid root

---

### Post by 67GTA on 2007-06-11
Try this link to fix your sudo problem first, then try the code I gave you to change your permissions: [http://ubuntuforums.org/showthread.php?t=228443&highlight=setuid+root](http://ubuntuforums.org/showthread.php?t=228443&highlight=setuid+root)
You may have to reset your root password after this(not sure). Have you added any users after installing?

---

