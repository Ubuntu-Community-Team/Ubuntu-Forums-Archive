---
title: "No executables are working!"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by skibblesx on 2008-03-07
I get the Linux files but when I click thn they never even try to start. Help!

---

### Post by thisiam on 2008-03-07
by executables do you mean files that end with .exe ?
you would need wine for them. 
or do you mean packages?

---

### Post by hyper_ch on 2008-03-07
By default files can't be executed, read up here:  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by 3rdalbum on 2008-03-07
Skibblesx: What file are you trying to run?

If you want programs for Ubuntu, go to the Synaptic Package Manager and install them from there.

In future it's a great help if you could provide as much information as possible about your problem, so we know how to help you.

---

### Post by skibblesx on 2008-03-07
I mean like getting the Linux version of Step Mania and others that made a program compatable with Linux.

---

### Post by PmDematagoda on 2008-03-07
Try executing the program using the terminal:-
```
sh nameofexecutable
```
or
```
./nameofexecutable
```

---

### Post by The Titan on 2008-03-07
You would also need to make them executable, do this by right clicking the file, going to the permissions tab and clicking Allow this file to be run as an executable box

---

### Post by corney91 on 2008-03-07
> **The Titan said:**
> You would also need to make them executable, do this by right clicking the file, going to the permissions tab and clicking Allow this file to be run as an executable box

Or, in the terminal:
```
sudo chmod +x [*name of file*]
```

---

