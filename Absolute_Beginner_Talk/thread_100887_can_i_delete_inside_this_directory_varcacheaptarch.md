---
title: "can i delete inside this directory? /var/cache/apt/archives"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-12-08
hi, can i delete all the archives from the directory below?:
/var/cache/apt/archives

if i'm in the directory now is this the correct command?
sudo rm -rf

---

### Post by ssam on 2005-12-08
```
sudo apt-get clean
```

might be slightly safer

---

### Post by Danielle on 2005-12-08
thanks, ssam. i was going to call the thread can i clean... but normally when i guess a command it's wrong :rolleyes:  so it is OK to do then? that's were apt-get installs from? thanks for the help.

---

### Post by ssam on 2005-12-08
from the man page

> clean  clean clears out the local repository of retrieved package files. It removes  everything    but    the    lock    file    from /var/cache/apt/archives/    and /var/cache/apt/archives/partial/. When APT is used as a dselect(8) method,  clean is  run  automatically.  Those  who  do  not  use dselect will likely want to run apt-get clean from time to time to free up disk space.

so it basically does the same thing, as your rm command, appart from leaving the lockfile alone.

it will do no harm, just that apt will need to redownload the debs again if you reinstall a package.

---

### Post by Danielle on 2005-12-08
OK, i understand now, i watched it as it cleaned the dircetory. clean is a much better command for that. thanks, ssam

---

