---
title: "removing ubuntu?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Corey4666 on 2006-09-13
i was curious how do you remove linux? cuz im on a dual boot with windows and ubuntu on the same harddrive 
i want to reinstall windows but i done that once before and when i boot up ubuntu and windows isnt a option to choose from it just boots up windows

so i need to know how to remove ubuntu uninstall it from the harddrive im thinking about getting 2 harddrives for each os

---

### Post by ruedu on 2006-09-13
I'm having some trouble understanding what you're saying here.  If I understand right, you're saying that you've removed GRUB, the menu system that allows you to choose which OS to boot.  Is that right?

---

### Post by b_martinez on 2006-09-13
> **Corey4666 said:**
> i was curious how do you remove linux? cuz im on a dual boot with windows and ubuntu on the same harddrive 
i want to reinstall windows but i done that once before and when i boot up ubuntu and windows isnt a option to choose from it just boots up windows

so i need to know how to remove ubuntu uninstall it from the harddrive im thinking about getting 2 harddrives for each os

If I'm reading this right , you have already re-installed Windows? If you did that automatically, then you already wiped Ubuntu. This may be why it goes to Windows right away. 
If you have a live cd, the way to check is pretty easy. Just boot the live cd, then once you are logged in, try

 sudo fdisk /dev/hda

at a terminal. I the output shows nothing besides a sinle partition, and shows as "NTFS/HPFS" then the total hard drive is windows.
If you don't have a live cd, boot into windows, go to "My Computer" and check to see how many hard drives it shows. If C:\ shows that it has the full size of your hard drive, you no longer have Ubuntu on it.
You can always use a win 98 boot disk to re-format the Ubuntu hard drive, and the have your windows install convert it to NTFS. Re-sizing the existing windows partition is also a possibility, but I don't know how to do that.
hthhttp://ubuntuforums.org/images/smilies/rolleyes.gif
Bill

---

