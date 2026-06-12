---
title: "how to install wine?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by feest on 2006-06-02
i have downloaded wine and tried several tutorials how to install it but they won't work how do i install wine easy tutorial please i'm an absolute noob

my filename of wine is

/home/sven/Desktop/wine-1.9.14.tar.bz2

please help

~sven

---

### Post by %hMa@?b&lt;C on 2006-06-02
the absolutely easyest way is to use Automatix
[http://ubuntuforums.org/showthread.php?t=177646](http://ubuntuforums.org/showthread.php?t=177646)
check that link out

---

### Post by Jagot on 2006-06-02
Wine is in Ubuntu's universe repository.  You will need to enable that ([http://www.psychocats.net/ubuntu/sources.php)](http://www.psychocats.net/ubuntu/sources.php)), then just:

```
sudo aptitude install wine
```

Then to configure it:

```
winecfg
``` [edited typo thanks to ctgray's post below]

If you want to learn more about installing stuff then go here:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Always check to see if something's available in the repositories first because it is the easiest way.

---

### Post by ctgray on 2006-06-02
winecfg

---

### Post by feest on 2006-06-02
yeah ok wine works but i have a problem, i can't browse on my drive they simply dont exist when i try to setup an application it needs to install to c:\program files\... but it pops up with an error saying invalid directory how can i solve this ](*,) ](*,) ](*,)

---

