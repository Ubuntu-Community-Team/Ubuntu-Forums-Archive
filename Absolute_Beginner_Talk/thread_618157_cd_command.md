---
title: "cd command"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by everest on 2007-11-20
The cd command is a bash internal command! what does it mean? I do not understand, please explain.

---

### Post by PmDematagoda on 2007-11-20
The cd command is what allows you to navigate between directories in the terminal. For example:-

cd.. -goes up to the directory which is found before the one you are currently in.

cd /name/of/folder -moves you to the folder where you wish to go

ls -displays the contents of the folder you are in

---

### Post by everest on 2007-11-20
> **PmDematagoda said:**
> The cd command is what allows you to navigate between directories in the terminal. For example:-

cd.. -goes up to the directory which is found before the one you are currently in.

cd /name/of/folder -moves you to the folder where you wish to go

ls -displays the contents of the folder you are in

I am not satisfied with your reply...I understand the use of the commands but still dont understand what internal command means.

---

### Post by yota on 2007-11-20
Most commands are actual binary executables stored in the filesystem, for instance when you type the "ls" command the bash (which is the command line interpreter) launches the program located in /bin/ls.
"cd" is instead an indication you give to bash to "change directory". Cd is not an executable, and there's no binary anywhere, you just tell the bash to move on a folder. These types of commands are called "internal" since they are entirely processed by the bash itself.

> 
yota@linbook:~$ which ls
/bin/ls
yota@linbook:~$ ll /bin/ls
-rwxr-xr-x 1 root root 78004 2007-09-29 14:51 /bin/ls
yota@linbook:~$ which cd


Hope this helps!

---

### Post by daimaru on 2007-11-20
cd = change directory

---

