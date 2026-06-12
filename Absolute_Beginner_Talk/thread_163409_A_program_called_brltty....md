---
title: "A program called brltty..."
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by didgeridoo on 2006-04-20
Well, I am not an absolute beginner, but I am somewhat new to Ubuntu (I am using Dapper 6.06).  Today I noticed a unusually large amount of memory being used and the culprit was ***brltty***.  I learned that, in short, it is a braille terminal to assist the blind.  Is this something that needs to run?  If so, why does it need so much memory?

---

### Post by catlett on 2006-04-20
If you don't have the disability it isn't neaded. If that is the programs full name you can ```
 sudo apt-get remove britty
```

---

### Post by htinn on 2006-04-20
If you try to remove brltty, you may have to remove ubuntu-desktop (or edubuntu-desktop if you're using that).

---

### Post by didgeridoo on 2006-04-20
This is the case, htinn.  Is it safe to remove the brltty link with /etc/rcS.d or does ubuntu-desktop need it actually running?

---

### Post by Qrk on 2006-04-20
ubuntu-desktop doesn't need anything. Its just a metapackage with no real content. Feel free to remove it along with brltty. 

If you want to upgrade to edgy in the future, remember to reinstall it as it helps prevent broken packages.

---

