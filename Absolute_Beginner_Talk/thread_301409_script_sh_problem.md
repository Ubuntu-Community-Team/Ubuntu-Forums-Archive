---
title: "script sh problem"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by jamaas on 2006-11-17
I'm attempting to install a program that is a couple of years old, that was installed from a shell script.  I've made it executable but get the following error when attempting to run it in a terminal window.  I realize that the shell in the terminal is bash, is this the cause of the problem?  Do I need to edit the sh file and change /sh to /bash?   Any other thoughts or suggestions most welcome.

Thanks

Jim

bash: ./CDInstall_2_0_linux.bin: /bin/sh: bad interpreter: Text file busy

---

### Post by marekdef on 2006-11-17
try this way
chmod u+x ./CDInstall_2_0_linux.bin
./CDInstall_2_0_linux.bin

---

### Post by jamaas on 2006-11-17
Thanks marekdef  	

Should have said, already done that, still have same problem.

Jim

---

### Post by taurus on 2006-11-17
Yes, change the first line from "#!/bin/sh" to "#!/bin/bash" and run it again.  However, if you want to install it on your system, outside of $HOME, then you need to use sudo...

```
sudo ./CDInstall_2_0_linux.bin
```

---

