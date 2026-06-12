---
title: "My openoffice doesn't work."
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by yjsyj on 2006-09-10
After I installed the lastest ATI driver, my OO refuses to work anymore.](*,) 

When I tried to run like word processor, I can see a window was open and said "starting OpenOffice...". But after that, nothing happen. Any one has same problem? I have reinstalled the OO by using Synapic, but it didn't solve the problem. What shold I do to fix this problem? :confused: I don't want to reinstall the ubuntu again. 

Thanks!

---

### Post by aysiu on 2006-09-10
I don't know what you should do to *fix* the problem, but you'd be in a much better position to *diagnose* the problem if you launch it from the terminal and look at the terminal output.

I believe the command is ```
ooffice -writer %U
```

---

### Post by rowanparker on 2006-09-10
I had this problem. It happens with older ATI cards.
See [here]("http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26").

---

### Post by yjsyj on 2006-09-11
Thanks guys.
I tried the command, but nothing happen. I'm going to try the driver one.
Thanks again.

---

### Post by yjsyj on 2006-09-11
OK, after downgrade the driver, OO works again. but my ATI driver back to Mesa again:

ubuntu@ubuntu-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

hmmm... is there any prossible to keep my ATI driver update and OO still wroks? 

anyway, I can use OO to work, I will find another way to install ATI driver.

---

