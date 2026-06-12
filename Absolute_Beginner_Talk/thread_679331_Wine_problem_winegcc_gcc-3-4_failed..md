---
title: "Wine problem winegcc: gcc-3-4 failed."
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by zFb on 2008-01-26
I have no idea what happened. I restarted then when entered winefile this popped up.
> 
winegcc: gcc-3.4 failed


---

### Post by zFb on 2008-01-26
I also found out anything i try to install comes back with this error
> dpkg: parse error, in file `/var/lib/dpkg/available' near line 3 package `binutils-static':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)


---

### Post by zFb on 2008-01-26
solved. This fixed it right up.
>  sudo dpkg --clear-avail && sudo apt-get update

---

