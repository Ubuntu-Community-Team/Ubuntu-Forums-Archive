---
title: "Wtf did ubuntu do to itself?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by ilyash on 2007-02-28
When I log in as root, I get an error.. Could not chdir to home directory /root: No such file or directory

also.. whenever i edit any file in Vi..

E138: Can't write viminfo file /root/.viminfo!


And I apparently don't have a ~/.bashrc as root...

whats going on? How do i fix it?

thanks!

---

### Post by sgstarling on 2007-02-28
So with your favorite file manager, it doesn't show a /root directory?

If so, that would explain why you cannot write to /root/.viminfo

Question is, what happened to /root?  Can you think of any rm comands you may have done recently? 

This...

is bad.

---

### Post by ilyash on 2007-02-28
yeah.. when i ssh to it... if i ls / i get:

/# ls
bin   cdrom  etc   initrd      lib         media  opt   sbin  sys  usr  vmlinuz
boot  dev    home  initrd.img  lost+found  mnt    proc  srv   tmp  var


anything I can do other than uninstall?

---

