---
title: "Mounting a network folder in WINE?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by raydeen on 2007-12-20
Have a question for the brain boxes here. I work at a votech school and the majority of our machines here are Macs. Of course the majority of the programs that our teachers want to use are Windows based. It's a never ending headache. At any rate, I've been able to get some electronics education software running on Macbooks through a combo of Virtualbox, Ubuntu, and WINE. After solving a few font issues, it's pretty much flawless. The program tests the students and can then save their results to a folder and print a certificate. The teacher would like to have all the student data in one place rather than spread out amongst the laptops. The software is pretty old and the file storage is controlled by an INI file. In this case, it knows to save the results to c:\grades in the WINE folder. Is there a way to create a link to a network folder that I could put in this INI file? I tried copying and pasting an SMB link but the software of course had no idea how to access the link. Any ideas? It's not mission critical, but if I could get this to work, it would be great and I'd learn a little something in the process.

---

### Post by PeterJS on 2007-12-20
You could use smbfs to mount the samba share some where in the local file system and then create a symlink between ~/.wine/drive_c/grades/something.ini and where ever you put the samba mount point.

---

### Post by raydeen on 2007-12-21
Many thanks! I thought it might be something like that. This'll give me something to mess around with over the Christmas break. :)

---

### Post by tech9 on 2007-12-21
> **raydeen said:**
> Have a question for the brain boxes here. I work at a votech school and the majority of our machines here are Macs. Of course the majority of the programs that our teachers want to use are Windows based. It's a never ending headache. At any rate, I've been able to get some electronics education software running on Macbooks through a combo of Virtualbox, Ubuntu, and WINE. After solving a few font issues, it's pretty much flawless. The program tests the students and can then save their results to a folder and print a certificate. The teacher would like to have all the student data in one place rather than spread out amongst the laptops. The software is pretty old and the file storage is controlled by an INI file. In this case, it knows to save the results to c:\grades in the WINE folder. Is there a way to create a link to a network folder that I could put in this INI file? I tried copying and pasting an SMB link but the software of course had no idea how to access the link. Any ideas? It's not mission critical, but if I could get this to work, it would be great and I'd learn a little something in the process.

you could try this samba command...

```
sudo mkdir /mnt/wine
```
```
sudo mount -t cifs -o username="you_user_name",password="your_password" //"IP address"/"share" /mnt/wine
```

---

