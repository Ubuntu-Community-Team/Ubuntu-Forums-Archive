---
title: "Owning mounted Windows OS disk"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Michl on 2007-02-25
I mounted my windows hard drive as follows
sudo mount -t ntfs /dev/hdb1 /media/windows
and when I cd and do ls, I can see the names
of files and folders in blue/purple.

But when in Places, COmputer and so on,  I 
am told I am not the owner.  How do I become
owner?  I thought that in the graphic interface
I was always in sudo and would be asked for
passwords, but I'm prompted for nothing.

Thanks,
Michl

---

### Post by Michl on 2007-02-25
Ok, I learned how to use alt-F2 and gksudo nautilus
to edit root files and change ownership and permissions.
So now I own that file.  But none of the files and folders
in windows show-up.

Michl

---

