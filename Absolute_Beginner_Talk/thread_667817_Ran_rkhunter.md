---
title: "Ran rkhunter"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by maineman2 on 2008-01-14
I ran rkhunter it said there was a warning and to check the logs. How do I check the logs. And if there is a warning What should I do Thanks Dan

---

### Post by bodhi.zazen on 2008-01-14
depends on the warning. Most of them are "normal" and can be ignored.

To read the logs :

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by SOULRiDER on 2008-01-14
The log should be:
```
 /var/log/rkhunter.log
```

---

### Post by maineman2 on 2008-01-14
I get the message permission denied di I have to log in as root for this? If so how do I di it thanks Dan

---

### Post by ajmorris on 2008-01-14
> **maineman2 said:**
> I get the message permission denied di I have to log in as root for this? If so how do I di it thanks Dan

Hi, yes, the log needs to be viewed as root, to do this, do this:
```
gksu gedit /var/log/rkhunter.log
```

---

### Post by SOULRiDER on 2008-01-14
You can also just view the warnings instead of the whole log with this command:
```
grep WARNING /var/log/rkhunter.log | less
```

---

### Post by maineman2 on 2008-01-14
The script does not work for viewing warnings only.Any help would be appreciated Thanks Dan

---

### Post by bodhi.zazen on 2008-01-14
Best post the exact warning.

---

### Post by maineman2 on 2008-01-18
I ran rkhunter and this is the result.

                  Checking for hidden files and directories       [ Warning ]
[22:24:56] Warning: Hidden directory found: /e.java
[22:24:56] Warning: Hidden directory found: /dev/.static
[22:24:56] Warning: Hidden directory found: /dev/.udevtc/
[22:24:56] Warning: Hidden directory found: /dev/.initramf


        I then ran root check and the results were negative. Any Ideas? Thanks Dan

---

### Post by bodhi.zazen on 2008-01-18
Those warnings are fairly typical and I do not think they are of concern.

[http://ubuntuforums.org/showthread.php?t=222785](http://ubuntuforums.org/showthread.php?t=222785)

[http://www.ubuntu-forums.net/showthread.php?t=496422](http://www.ubuntu-forums.net/showthread.php?t=496422)

---

