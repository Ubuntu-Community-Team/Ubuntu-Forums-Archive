---
title: "Help !! Error : 15"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-10-17
Ok,restored the Ubuntu drive,now getting error 15 so can't get grub installed to boot !!  Thanks ! :)
Edit: restored XPmbr,booted to Dapper Live disc, terminal>sudo grub>find /boot/grub/stage1>Error:15

---

### Post by Drakkor on 2006-10-17
*boot*

---

### Post by Sef on 2006-10-17
> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

Looks like there was an error in the way GRUB got set up. Try this to [restore GRUB.]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by Drakkor on 2006-10-17
Thanks for the reply,Sef,tried that,but only could see the first hd,hda and Ubuntu is on hdb,but......Whooohooo !! :p restored hdb again,and booted to Ubunutu live disc, and viola, found (hda1,0),back in business, reinstalled the grub just fine,and now i'm in Ububntu !! :p

---

