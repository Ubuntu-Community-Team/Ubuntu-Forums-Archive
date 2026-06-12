---
title: "[SOLVED] Can't get into Wine Program Files directory in terminal"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by captainwitherspoon on 2007-07-29
For some reason I can't get into my Program Files directory in the terminal. 
```
z@xZx:~/.wine$ cd
z@xZx:~$ cd .wine/drive_c
z@xZx:~/.wine/drive_c$ ls
Program Files  windows
z@xZx:~/.wine/drive_c$ cd Program Files
bash: cd: Program: No such file or directory
z@xZx:~/.wine/drive_c$ cd Program_Files
bash: cd: Program_Files: No such file or directory
z@xZx:~/.wine/drive_c$ 

```
WTF??

---

### Post by Kilz on 2007-07-29
> **captainwitherspoon said:**
> For some reason I can't get into my Program Files directory in the terminal. 
```
z@xZx:~/.wine$ cd
z@xZx:~$ cd .wine/drive_c
z@xZx:~/.wine/drive_c$ ls
Program Files  windows
z@xZx:~/.wine/drive_c$ cd Program Files
bash: cd: Program: No such file or directory
z@xZx:~/.wine/drive_c$ cd Program_Files
bash: cd: Program_Files: No such file or directory
z@xZx:~/.wine/drive_c$ 

```
WTF??

It is a problem, but you can click Go > Location and a address bar will open in nautilus. Then type ~/.wine and the wine folder will open. You can then visually navigate to the file.

---

### Post by shirilover on 2007-07-29
Try just typing the first three letters and hitting the Tab key, or use the escape character \ before the space in Program Files like -> Program\ Files

---

### Post by aos101 on 2007-07-29
I think it's because there is a space in the folder name, so the ls command thinks the two words are seperate parameters to the command (that's why it says *"Program: No such file or directory"*, because it tried to change to a directory called Program).  

Putting the directory in double quotes should work (cd "Program Files"), although using the tab key is usually quicker.

---

### Post by tomcheng76 on 2007-07-29
becoz the shell will look for space
space act like seperator
you need to either escape it or use ""
cd "Program Files" or cd Program\ Files

---

### Post by captainwitherspoon on 2007-07-29
AHA! Thankyou!

---

