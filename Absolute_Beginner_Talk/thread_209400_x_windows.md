---
title: "x windows"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by seanm on 2006-07-05
hi all,

does any one know why i get the following when i try to use x-windows?

X-Win32 version 5.4 patch level 3
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x0
  Serial number of failed request:  65
  Current serial number in output stream:  66


when i try and check xterm on the remote end i get:-

xterm Xt error: Can't open display: 
xterm:  DISPLAY is not set

I have tried to run xterm in root as well as non root but i get the same messages

any ideas would be helpful

thanks

Seanm:(

---

### Post by lamego on 2006-07-05
After logging into the remote system on the terminal type:
```
export DISPLAY=your_ip:0
```

This will tell tho the X applications on the remote system that the graphical interface must be sent to the X display 0 running at your_ip .

---

