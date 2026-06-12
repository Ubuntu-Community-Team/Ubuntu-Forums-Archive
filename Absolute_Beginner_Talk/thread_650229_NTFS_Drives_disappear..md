---
title: "NTFS Drives disappear."
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by thorosius on 2007-12-26
Hy!
 
OK I have gutsy and it automatically detects my NTFS drives and mounts them but sometimes when I boot up, NTFS drives aren't mounted and I need them mounted all the time. Can anyone help?

---

### Post by TidusBlade on 2007-12-26
Maybe you didnt shut down Windows properly, might be that, since mine dont mount if I dont shut down windows properly...

---

### Post by kpkeerthi on 2007-12-26
What happens when you type **sudo mount -a** in a terminal?

---

### Post by LaRoza on 2007-12-26
> **TidusBlade said:**
> Maybe you didnt shut down Windows properly, might be that, since mine dont mount if I dont shut down windows properly...

Boot into Windows: type "chkdsk /F x:" in the terminal (use whatever drive letter it is, not x)

---

### Post by TWO on 2007-12-26
> **TidusBlade said:**
> Maybe you didnt shut down Windows properly, might be that, since mine dont mount if I dont shut down windows properly...

Yeah. The last time that Ubuntu didn't load the NTFS partition for me was because I had forgotten that I had put Windows into "Hibernate" mode for whatever reason.

---

### Post by thorosius on 2007-12-27
> **TidusBlade said:**
> Maybe you didnt shut down Windows properly, might be that, since mine dont mount if I dont shut down windows properly...
 
Checked this up and yes this is the case, whenever I dont shut down Windows properly this problem occurs.
And entering sudo mount -a says that the NTFS drives are flaged as being used.
 
Thanks for the help everyone!

---

### Post by yamfox on 2007-12-27
Installing NTFS 3G Driver

    *

      Enable the universe repository and install the ntfs-config package. See Installing Software.
    *

      Click Applications &#8594; System Tools &#8594; NTFS Configuration Tool
    *

      The upcoming tool will detect NTFS partitions on your system. Check each partition you wish to access, and, if you wish to, click the mount directory to change it. When finished, click Apply.
    *

      On the next screen Enable write support for internal device will be selected by default. Click OK.

Your NTFS drive will be now be available in the mount point you selected.

---

### Post by thorosius on 2007-12-27
> **yamfox said:**
> Installing NTFS 3G Driver
 
*
 
Enable the universe repository and install the ntfs-config package. See Installing Software.
*
 
Click Applications &#8594; System Tools &#8594; NTFS Configuration Tool
*
 
The upcoming tool will detect NTFS partitions on your system. Check each partition you wish to access, and, if you wish to, click the mount directory to change it. When finished, click Apply.
*
 
On the next screen Enable write support for internal device will be selected by default. Click OK.
 
Your NTFS drive will be now be available in the mount point you selected.
Regardless of how I shutdown WinXP? Won't it cause any issues on a dual boot?

---

### Post by yamfox on 2007-12-27
Nope :D
Changing the mount point doesn't change the location, It's more like it's making a shortcut

---

