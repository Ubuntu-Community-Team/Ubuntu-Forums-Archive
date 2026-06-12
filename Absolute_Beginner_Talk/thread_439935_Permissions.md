---
title: "Permissions"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by L115A1 on 2007-05-11
Please excuse my ignorance as I have just installed Feisty as a direct replacement for XP. I'm having issues with changing folders and the installation of software.  My question is; how do I ensure that I have complete access to my file system? 

Thanks

P

---

### Post by Najand on 2007-05-11
You can always check the permission of files and directories using 
```

ls -l <FILE>

```
command. Ofcourse you need to change <FILE> with your file or directory name.

---

### Post by L115A1 on 2007-05-11
Thanks

---

### Post by renzokuken on 2007-05-11
to have access to whatever you need when you do it simply use the sudo command before each action (only valid for terminal commands)

e.g.

sudo nano /etc/apt/sources.list

could you be more specific about which fies and folders you need access to and why and which software you are installing

---

### Post by L115A1 on 2007-05-11
I'm trying to install Firestarter at the moment, and as to why I need complete access to my system, well it's my machine... 

Thanks 

P

---

### Post by Najand on 2007-05-11
You need to use "sudo" before your commands! 
If you ever had any other questions, feel free to ask us.

---

### Post by L115A1 on 2007-05-11
Got it working fine now, I just played with everything until it complied.

Thanks

---

