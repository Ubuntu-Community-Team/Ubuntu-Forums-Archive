---
title: "Can't remove file files from file system"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by kuruyiva on 2008-04-09
every time to move a file in the trash, I receive this message informing me that I don't enough rights to do so, how can I get control over file system.

---

### Post by meho_r on 2008-04-09
You have to change permission of file and for that you need root privileges. E.g. if you have a file named "file.txt" on your Desktop (and your user name is "kuruyiva", you can change permission this way:

Open the Terminal (Applications > Accessories > Terminal) and type: 

```
sudo chmod 777 /home/kuruyiva/Desktop/file.txt
```

Fot other place you have to enter correct path to the file.

Try now to delete the file usual way.

EDIT: As others have warned, be very careful when deleting files and delete ONLY files that are in your home folder and you are sure about them.

---

### Post by gunksta on 2008-04-09
I'm curious about the context of your question. What file are you trying to remove? (Location)

---

### Post by Sinkingships7 on 2008-04-09
this code will give you complete permissions to all files. be careful with it. do what you need to do and get out.

```
sudo nautilus
```

EDIT: you're not trying to delete something that's not in your home folder, are you?

---

### Post by gunksta on 2008-04-10
That's why I started asking for the context of what the OP is trying to accomplish. I don't think we should accidentally help someone hose their system. Before anyone offers any more advice on how to delete system files, we should find out what they are trying to delete.

---

### Post by brian_p on 2008-04-10
> **kuruyiva said:**
> every time to move a file in the trash, I receive this message informing me that I don't enough rights to do so, how can I get control over file system.

sudo will give you sufficient control. In fact you will have enough control to destroy other users files or obliterate the system. You would have to have a very, very good reason for deleting a system file. Maybe someone could think of one, I can't.

---

