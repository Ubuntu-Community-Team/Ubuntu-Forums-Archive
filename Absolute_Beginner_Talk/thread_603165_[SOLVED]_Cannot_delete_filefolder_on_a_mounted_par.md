---
title: "[SOLVED] Cannot delete file/folder on a mounted partition"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by rockballad on 2007-11-04
Hi all,

I have an ext3 partition, /dev/sda5. After I mount it to /data, I can create a file/folder in it. But I can't delete it. The error is:

> 
Error while moving items to "/data/.Trash-ubuntulaptop".
You do not have permissions to write to this folder.
[ OK ]


ubuntulaptop is my laptop name.

When I "sudo nautilius" and go to /data folder, I can delete file/folder.

So I guess it's user permissions problem. Is there a folder called "/data/.Trash-ubuntulaptop". How can I change permission for it? 

Thanks

---

### Post by ubuntology on 2007-11-04
Run this in a terminal window while it's mounted.
sudo chmod 777 /data/.Trash-ubuntulaptop

---

### Post by Hospadar on 2007-11-04
the problem is you don't have privileges for anything outside your home directory by default.  There should be a .Trash folder (and if there isn't, creating it might be where the priviledge issue is, but the chmod as above (you could even just do a "sudo chmod -R 777 /data" that would change the permissions for everything on that drive you mounted there.

---

### Post by rockballad on 2007-11-05
> **Hospadar said:**
> the problem is you don't have privileges for anything outside your home directory by default.  There should be a .Trash folder (and if there isn't, creating it might be where the priviledge issue is, but the chmod as above (you could even just do a "sudo chmod -R 777 /data" that would change the permissions for everything on that drive you mounted there.

Thanks a lot for your detailed help.

Thank ubuntology, too. 

Thanks to your all help, my problem solved!

Best regards,

---

