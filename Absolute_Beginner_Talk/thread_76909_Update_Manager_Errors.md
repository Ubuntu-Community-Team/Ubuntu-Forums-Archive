---
title: "Update Manager Errors"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by czambran on 2005-10-15
Once in a while when I run the Update Manager and click on reload I get the following error:
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Can anybody please tell me if I am doing something wrong?

Christian

---

### Post by Manny C on 2005-10-15
Do one or both of the following:
```
 sudo apt-get clean 
```
```
 sudo apt-get update 
```

I find that the first usually helps more often than not. Someone care to explain how and or why?

---

