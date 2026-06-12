---
title: "permissions"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by ice.man on 2006-04-19
how to change folder permissions and add them to ur group (username)

---

### Post by Sutekh on 2006-04-19
To **ch**ange **mod**es of access (permissions) use chmod
```
chmod -R ### /<some folder>
```
 - the **-R** makes the command recursive through all children folders

 - In place of the ### put the number corresponding to the desired permissions using a [chmod calculator](http://www.onlineconversion.com/html_chmod_calculator.htm)

To **ch**ange **own**ership use chown
```
chmod -R user:group /<some folder>
```

---

### Post by steve.horsley on 2006-04-19
Command line answer:
Changing file/folder permissions is done with **chmod**. Examples might be **chmod 750 myfile** or **chmod +x myprog**. Use **man chmod** to see the manual. Changing owner or group of a file/directory is done with **chown** or **chgrp**. chown can change both the owner and group at once, e.g. **chown steve:steve myfile**.
You may have to run these commands under **sudo** to get the privilege needed to change ownerships etc. e.g. **sudo chown steve:steve myFileNow**.

GUI answer:
Right-click the file or directory in the Nautilus file manager, and select properties. Look at the Permissions tab. You may need to run nautilus with root privilege to have hte rights to change ownerships etc, with this command line:
**gksudo nautilus**
Yes, you're back to the command line to launch the GUI app.

---

### Post by macdo on 2006-04-19
Or you can open a root nautilus from the Run Application box: alt+F2, then type in ```
gksudo nautilus
```

---

