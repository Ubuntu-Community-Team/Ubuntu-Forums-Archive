---
title: "edgy uh oh! (partition help/grub error 22)"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by oranguman on 2007-02-27
i've been bad.. 

in an effort to remove my windows partition and make ubuntu my primary, I moved the ubuntu partition via gparted's copy and paste, to make it start at 0 bytes and take up the whole disk.. 

in retrospect, I guess it is asking a bit much to have grub magically find this out and boot up as before.. I get 'error 22' on boot and that's that. 

I need to know how to point grub toward the new partition for booting, the correct one being flagged in my fdisk output below as 'boot'. 

"ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4762    38250733+  83  Linux
/dev/hda3            4763        4864      819315    5  Extended
/dev/hda5            4763        4864      819283+  82  Linux swap / Solaris
"

i'm here watching the thread so ask away.

---

### Post by mikewhatever on 2007-02-27
At grub boot screen, choose to boot Ubuntu and press 'e' to edit boot options. Edit the (hd0,X) part, to (hd0,0) and try booting by pressing 'b'. If it works, edit grub menu to make the change permanent.
gksudo gedit /boot/grub/menu.lst

---

### Post by oranguman on 2007-02-27
there is no boot menu. Grub hangs with an Error 22 while booting. 

/boot/grub/menu.lst  is empty.

should I be looking to reinstall grub?

---

### Post by mikewhatever on 2007-02-27
I think so.

---

### Post by oranguman on 2007-02-27
thanks? 

edit: I want to direct readers of this thread to [http://ubuntuforums.org/showthread.php?t=224351&highlight=how+to+reinstall+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=how+to+reinstall+grub)

which is seeming really useful for those of us who have messed up their master boot record (that's MBR for short :)


further edit: YESSSSSSS! I GOT IT TO WORK! 

hooray!

here were the steps, for anyone that makes the same error as I did:

1. Reinstall GRUB from live CD onto newly named HDD (using thread above)
       -making the boot menu accessible
2. Edit boot options for Ubuntu from this menu. In this case I changed the "hd" as well as the "main directory" from "0,1" to "0,0" and from "hd2" to "hd1"...  the new values will mirror the "find" output from the GRUB shell. 
3. edited the grub menu to make these changes permanent. 

simple! thanks for the help.

---

### Post by kittyhawk63 on 2007-02-27
> **oranguman said:**
> thanks? 
edit: I want to direct readers of this thread to [http://ubuntuforums.org/showthread.php?t=224351&highlight=how+to+reinstall+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=how+to+reinstall+grub)
which is seeming really useful for those of us who have messed up their master boot record (that's MBR for short :) have a nice day.

Oranguman,
You need to mark your post as "Resolved." Start like your going to edit, go to Advanced Edit, and choose toward the top "Mark as Resolved." People will know your question is answered and they will also know that they can look at your post for an answer that may solve their problem. gud daay!
KH

---

