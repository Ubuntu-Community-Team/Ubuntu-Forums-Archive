---
title: "Wine error"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Drewat17 on 2007-06-13
After I installed WIne 0.9.38 i tryed to run it from the terminal and came across an error message that stated **_wine: could not load L"c:\\windows\\system32\\program.exe": Module not found_**

---

### Post by machoo02 on 2007-06-13
how did you try to run wine?  Please give a little more detail.  what were you trying to install or run through it?

---

### Post by Drewat17 on 2007-06-13
Well i went into terminal and then typed "wine program" and thats when the error message came up

---

### Post by dfreer on 2007-06-13
Did you literally type:
```
wine **program**
```

If so, the correct syntax would be to type the word "wine", and then type the path to the program you are trying to run and the program's name. So let's say I have a program called "windowssetup.exe" on my Desktop. This would be the command I'd run:
```
wine ~/Desktop/windowssetup.exe
```

---

### Post by Trueno22 on 2007-06-13
are you trying to program aka configure it??

if you are use winecfg

---

### Post by Tmi on 2007-06-15
EDIT: Solved my problem with "sudo apt-get remove --purge wine" and then a new install ow wine.

Old message;
I have the same kind of error. I'm not really sure when it started to behave like this since I've mostly used wine on my laptop for a while.

Here is how it looks:

```
tommi@Origin:~$ wine Desktop/DCPlusPlus-0.698.exe 
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/tommi', starting in the Windows directory.
wine: cannot find 'Desktop/DCPlusPlus-0.698.exe'
tommi@Origin:~$ 
```

---

