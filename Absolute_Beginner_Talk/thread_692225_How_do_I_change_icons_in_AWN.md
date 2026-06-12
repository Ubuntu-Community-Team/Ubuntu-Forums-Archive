---
title: "How do I change icons in AWN?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-02-09
I know "how" to, in the sense that you click the "change icon" button, but I don't know what files to look for.  For instance I added a launcher for the container-encryption program "Truecrypt 5.0".  When Truecrypt is running it has a customized icon that rests in the launcher area of AWN.  However I'm not sure how to find that image.  I'm not even sure what files I need to look for to setup/change the icons of any of the programs.  I know in Windows they were .ICO files, but with Ubuntu I haven't a clue.

Thanks in advance :)

---

### Post by Tenken on 2008-02-09
In Linux you can use .png or .svg files, and the icons for most programs are located in /usr/share/icons, and if you installed any custom themes they are in ~/.icons

---

### Post by BDNiner on 2008-02-09
I don't know how you created the launcher but some default icons are kept in /usr/share/piximaps. Icons files are normally .PNG. If you want to find the icons for Truecrypt you can create a launcher on the desktop and then open the properties for that launcher. the icon button will take you to the path that contains that icon. i hope that helps.

---

