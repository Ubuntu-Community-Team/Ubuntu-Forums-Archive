---
title: "what is debian_chroot?"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by shrikantubuntu on 2005-08-08
I want to know more about debian_chroot. When I type
echo $debian_chroot 
then it gives nothing. Why so?  :confused: 

Thanks

---

### Post by MrCheese on 2005-08-08
[QUOTE=shrikantubuntu]I want to know more about debian_chroot. When I type
echo $debian_chroot 
then it gives nothing. Why so?  :confused: 

Thanks[/QUOTE]

from [http://www.braincells.com/debian/tips/](http://www.braincells.com/debian/tips/) ............

Using The chroot Environments on Debian Machines

To use the chroot environments set up on the Debian machines run the dchroot program. In each chroot, there is a file /etc/debian_chroot, the contents of which will tell you which chroot you are in (see /etc/profile for an example of how to add this to your prompt).

---

