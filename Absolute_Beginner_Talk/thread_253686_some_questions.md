---
title: "some questions"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Somenoob on 2006-09-08
Is there no common executable file in linux?(Like Window's exe) only packaged files?

---

### Post by UltraMathMan on 2006-09-08
Ubuntu is based on Debian and I believe the equivalent of what you're referring to is the .deb

-Hope this helps :)

---

### Post by Somenoob on 2006-09-08
> **UltraMathMan said:**
> Ubuntu is based on Debian and I believe the equivalent of what you're referring to is the .deb

-Hope this helps :)

yes, but is that not a archival format?(like zip)

---

### Post by whizbaby on 2006-09-08
*Executable* is not a suffix in linux but a property of files that is permitted or not.

rwxr-xr--  1 root loot   76520 2006-05-05 19:50 foo

This here means that the command **foo** may be read, written to or executed by the user root, read or executed by members of the group loot and read by anyone. So executability depends on the permissions. Every file could be made executable, making sense or not...

---

### Post by UltraMathMan on 2006-09-08
Iirc, .deb is the format of the packages from which software is installed (using dpkg or apt-get, Synaptic, aptitude, etc.) it serves the same function as a .exe file. (anyone?)

---

### Post by whizbaby on 2006-09-08
Binary files and scripts are most likely to make sense to be executable. They are found in:
for common commands and most applications
/bin
/usr/bin

for more administrative commands:
/sbin
/usr/sbin

.deb packages are archives, so comparing them to .exe would not be so appropriate (What would the execution of an archive mean?).

---

### Post by UltraMathMan on 2006-09-08
Thanks for the correction/clarifiction whizbaby.

---

