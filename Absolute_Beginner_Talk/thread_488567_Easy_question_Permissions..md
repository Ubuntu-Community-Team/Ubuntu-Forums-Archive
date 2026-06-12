---
title: "Easy question: Permissions."
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-06-30
I want to extract a Tremulous map file to a place in the filesytem (the Tremulous folder), but it says I don't have permission. 

How do I get permission?

---

### Post by supersonicdarky on 2007-06-30
in terminal
```
sudo <command>
```

or if you are trying to extract with **file-roller**, press **alt+f2**, type **gksudo file-roller**, open the file that you want extracted with it, and then extract wherever you want

---

without sudo you cant modify anything outside of /home/ and /media/

---

### Post by aberadam on 2007-06-30
Thanks, but it doesn't work:

> adam@adam-desktop:~$ sudo <command>
bash: syntax error near unexpected token `newline'
adam@adam-desktop:~$ 




Can the permission be reversed afterwards?  I don't want/need permission to mess around with the filesystem most of the time.

---

### Post by supersonicdarky on 2007-06-30
you lose the privilages after a minute or two

also, the **<command>** is to be replaced with a command. you would probably find the gui approach easier, so follow that instead.

---

### Post by aberadam on 2007-06-30
Thanks, but I can't get the second method to work either.

---

### Post by aberadam on 2007-06-30
Can you give simpler instructions?

---

### Post by aberadam on 2007-06-30
The gui method you describe allows me to extract, but not 'far enough in' to the filesytem.  I need to put it in the Tremulous folder. 

Surely there's a simple way to allow access temporarily... this is Ubuntu, the OS that gives you control of your computer...

---

