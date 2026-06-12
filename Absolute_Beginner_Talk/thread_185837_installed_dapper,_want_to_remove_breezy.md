---
title: "installed dapper, want to remove breezy"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by markfasano on 2006-06-01
I've just installed Dapper Drake, but my GRUB menu is getting pretty crowded. I want to remove Breezy. How do I do that without screwing something up royally? Thanks.

---

### Post by Iowan on 2006-06-01
Cleaning up the GRUB menu *shouldn't* be too tricky - just edit the undesired lines out of menu.lst (make a backup copy first).  If it works, you'll want someone more knowledgeable to share how to clean up the obsolete files, etc.

---

### Post by Dr. Nick on 2006-06-01
Im betting you upgraded breezy to dapper and in that case have a few extra kernels laying around. Their is no need to remove breezy as it really doesnt exist if you upgraded it to dapper. 

To clean up grub you have a few choices.

If you are sure everything is working right curently and the kernel is good then open synaptic and search "linux-image" and you can select the old kernel version to uninstall. That will automatically take it out of the grub menu. Just dont remove the kernel you are in at the time

If you dont want to do that then just open the file /boot/grub/menu.lst in a text editor using sudo and you can just erase the old lines out of it that way.

If you want to get rid of excess packages left over look into deborphan and gtkorphan, plenty of info on the forums

---

