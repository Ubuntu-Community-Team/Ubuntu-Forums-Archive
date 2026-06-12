---
title: "Some problem"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by wongpk on 2006-07-22
Hello there, I'm new to ubuntu. So here are some of my questions, hope any expert here can answer it.

1, Once I type "su" in the terminal, it prompt out asked for password, but I can't type anything. Why? (Damange when I install ubuntu?)

2, How excatly to install wine? I searched this forum and wine website, don't really get it. Maybe I installed it already, but it just don't work when I tried to install my Adobe program. It freeze on the "Preparing to install..." as in Windows.

Thank you!

---

### Post by orb9220 on 2006-07-22
[http://ubuntuforums.org/showthread.php?t=78611](http://ubuntuforums.org/showthread.php?t=78611)

Step by step for install ing wine.

---

### Post by OU812 on 2006-07-22
2. I don't use wine. Sorry, I can't help

1. In ubuntu, there is no actual root account. That's why you can't use "su".  Use "sudo" instead. For example

Instead of
```
su
[root_password]
make install
```

do this
```
sudo make install
[user_password]
```

Note: Use your user password when you launch system, too.

john

---

### Post by theconley on 2006-07-22
As stated above: use sudo.

However, you can do an su, it's just typical that the shell won't show your typing for security reasons.  You were probably expecting asteriks.

~Conley

---

