---
title: "iso =&gt;ipod?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by fnordportland on 2006-12-14
im trying to get the files out of an iso so i can put them onto a ipod,id throw them on a cd but im all out and poor.thanks

---

### Post by evolvedlight on 2006-12-14
Hey

To get your files in a "normal" filemanager, follow these steps:
1)
Go into terminal: Accesories->Terminal
2)
Type: ```
sudo mkdir /media/ISO
```
3)
Type ```
sudo mount -o loop -t iso9660 /home/<yourusername>/theiso.iso /media/ISO
```
but replacing /home/<yourusername>/theiso.iso with the path to the iso file

4) You can now browse the contents of the CD under /media/ISO, and copy to an IPod if needed

Need any more help? PM Me

S

---

