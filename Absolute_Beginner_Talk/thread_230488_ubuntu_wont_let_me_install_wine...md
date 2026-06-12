---
title: "ubuntu wont let me install wine.."
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by kingvicious on 2006-08-06
well when i go to the add/remove program and i search for wine windows elumator i find it but when i mark to for download and install i get this error

'wine' is not available in any software channel

The application might not support your system architecture.

how do i fix this?

---

### Post by Jagot on 2006-08-06
What processor do you have?  As far as I know Wine only supports 386/686.

If that's what you have, Wine is in the universe repo.  Enable it with either of these links:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

Then, from Terminal:

```
sudo aptitude update
sudo aptitude install wine
winecfg
```

---

### Post by kingvicious on 2006-08-06
well i have a 64 bit amd proccesor

---

### Post by Jagot on 2006-08-06
Are you running the 32 bit version of Ubuntu or the AMD64?

---

### Post by kingvicious on 2006-08-06
iam running the 64 bit version of unbuntu

---

### Post by Jagot on 2006-08-06
This seems to be the way for AMD64:

[http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)

---

