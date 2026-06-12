---
title: "Cannot mount volume"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Quotidian Minutia on 2008-02-14
I'm very new, and trying to learn as I go, but not having much luck searching the forum and documentation.  Here's my latest hurdle:

I want to use an external hard drive, that I've previously filled up with lots of files (back in my Windows days).  I plug it in, turn it on, and get the error message in the attached screenshot.

I have absolutely no idea what any of that means, much less how to fix it!

---

### Post by hyper_ch on 2008-02-14
it says you can try the force option in there...

but then, I would plug it first into a windows machine and check the drive.

---

### Post by Quotidian Minutia on 2008-02-14
Check the drive for what?  I know it's working perfectly OK when I use it on my windows laptop.

---

### Post by jw5801 on 2008-02-14
You should just need to unmount it cleanly from a windows install (using the "safely remove hardware" dialog). Windows sets an in-use flag on ntfs filesystems when it's using them, so if Windows crashes (or you suspend or hibernate from it) then you won't be able to access the partition from anywhere else. Try the force option if you don't have easy access to a Windows install.

If you've done that, then there shouldn't be any harm in forcing it to mount.

---

### Post by kpkeerthi on 2008-02-14
Boot into (dirty) windows again. Plug the drive in and "Safely remove [that] hardware" and use it in Ubuntu.

---

