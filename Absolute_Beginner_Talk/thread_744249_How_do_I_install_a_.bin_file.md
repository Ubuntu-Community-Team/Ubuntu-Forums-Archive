---
title: "How do I install a .bin file"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2008-04-03
Bin files are linux executable files. You just have to make it executable(as in provide proper permissions) and then run it. ```
chmod +x filename.bin && ./filename.bin
``` so for your jre file it will be
```
chmod +x jre-6u3-linux-i586.bin && ./jre-6u3-linux-i586.bin
```

---

### Post by Tristam Green on 2008-04-03
unless im mistaken, you should be able to search for java in your package manager.

in gnome i did ```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
``` and it handled the dependencies and installed correctly.

good luck :)

---

### Post by Jeremy Jackins on 2008-04-03
alternatively, if you are confused by the chmod stuff, you can right click the file, go to the permissions tab, and check the box that says 'Excecute'. from there you can run the file in the terminal with ./filename.bin

edit: Tristam's way is probably best though, for ease of updating and uninstalling.

---

