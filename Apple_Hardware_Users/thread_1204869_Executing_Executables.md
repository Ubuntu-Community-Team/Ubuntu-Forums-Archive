---
title: "Executing Executables"
date: 2009-07-05
forum: Apple Hardware Users
---

### Post by 3Davideo on 2009-07-05
I have a DOS/Executable file I want to open.  At first, I could only open it in Archive Manager, because I could not right click (I have a Mac with a wireless Mighty Mouse, which won't register; I used another one-button mouse).  I found the delayed right click accessibility function, and used it.  I chose open with other application, and it gave me a list of other applications.  But I don't want to use another application; I want it to be its own application!  There's a command thing, but I don't know what to do with that.  Any help?

---

### Post by tiagobt on 2009-07-05
You can't run a Windows/DOS executable in Linux natively. You could try to use a Windows emulator, like Wine.

To install Wine, run the following command:
```
sudo apt-get install wine
```

Then run your executable file with Wine:
```
cd [folder where the file is located]
wine [file name]
```

For example:
```
cd /home/user
wine app.exe
```

---

### Post by cyberdork33 on 2009-07-06
even better, if it is really a DOS executable, it might be easier to use DOSBox.

---

