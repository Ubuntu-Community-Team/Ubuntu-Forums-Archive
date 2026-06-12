---
title: "Access Denied.......need help"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by 12hello on 2007-07-09
i am not able to make directories in the filesystem folder getting access denied how do i take full access of th file system folder i am using ubuntu 7.04

---

### Post by felicity on 2007-07-09
From the command line preface your commands with:
```
sudo
```

---

### Post by AlexenderReez on 2007-07-09
try to learn about sudo

> man sudo

---

### Post by 12hello on 2007-07-09
I have some files on the pen drive how do i move it to .... the root folder if i want todo it graphically

---

### Post by 3rdalbum on 2007-07-09
Use the command:

```
gksudo nautilus
```

Within the window that opens, you will be able to create, modify or delete any file on your filesystem. Open your flash drive in another Nautilus window, and drag your files from there onto the gksudo nautilus window.

---

### Post by 12hello on 2007-07-09
Please type "accept" to accept the terms and conditions of license agreement; Type "decline" to exit. accept
 
This installation requires 94 MB of free disk space.
 
Enter installation directory for Adobe Reader 7.0.0 [/usr/local/Adobe/Acrobat7.0] 
 
Directory "/usr/local/Adobe/Acrobat7.0" does not exist.
Do you want to create it now? [y]  y
mkdir: cannot create directory `/usr/local/Adobe': Permission denied
 
ERROR: Cannot make directory "/usr/local/Adobe/Acrobat7.0".
 
Enter installation directory for Adobe Reader 7.0.0 [/usr/local/Adobe/Acrobat7.0]             










i am getting this error what should i do ?

---

### Post by AlexenderReez on 2007-07-09
> **12hello said:**
> Please type "accept" to accept the terms and conditions of license agreement; Type "decline" to exit. accept
 
This installation requires 94 MB of free disk space.
 
Enter installation directory for Adobe Reader 7.0.0 [/usr/local/Adobe/Acrobat7.0] 
 
Directory "/usr/local/Adobe/Acrobat7.0" does not exist.
Do you want to create it now? [y]  y
mkdir: cannot create directory `/usr/local/Adobe': Permission denied
 
ERROR: Cannot make directory "/usr/local/Adobe/Acrobat7.0".
 
Enter installation directory for Adobe Reader 7.0.0 [/usr/local/Adobe/Acrobat7.0]             










i am getting this error what should i do ?

i think you want to install adobe reader right?please refer medibuntu.com

---

### Post by 12hello on 2007-07-09
hey i did go to mediubuntu .... but the index does not have anthing

---

