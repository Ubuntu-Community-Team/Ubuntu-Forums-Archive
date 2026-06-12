---
title: "Edit /etc/fstab to stop booting error"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by smokey_58au on 2007-08-24
I have made an error in my fstab file and I know what I need to change to fix it but problem is I now can't boot into my system to edit it.  Choosing recovery mode doesn't work as the boot still fails and if I choose command line I don't see an option to mount a volume and/or edit a file.  Can anyone tell me how to edit the file without booting into the system please?

---

### Post by wormser on 2007-08-24
You can boot into the live CD then edit.

---

### Post by smokey_58au on 2007-08-24
Ta, I thought that might be the case.  Does it matter that my CD is Dapper and my current installed version is Fiesty?  Also, what commands do I use to access the file on my hard drive?

---

### Post by wormser on 2007-08-24
No, it does not matter what version or distro of linux you use.  It has been a while since I have done that but I believe the installed OS will be under /mnt.  The installed OS  is mounted inside of the live CD.  So, make sure you are not editing the live CD fstab file.  Just cd into the directory then use nano to edit.

---

