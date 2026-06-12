---
title: "Dualbooting..."
date: 2010-12-13
forum: Apple Hardware Users
---

### Post by Dissident85 on 2010-12-13
Hi all, I have just installed ubuntu 10.10 onto my macbook pro. The install went great it detected osx on sda2 and added an entry into grub. 

But when i try to boot into osx, its a little weird and seems to just hang. when i select the osx option in grub a bunch of text comes up but like all the kernel modules loading in linux then it comes to a point where it says "Waiting for boot volume with UUID "blah blah blah

and sometimes after a while ill get "still waiting for root device"

any ideas on how i can fix this? 

thanks in advance. 

oh and by the way, they way i installed the system was to use the boot camp assistant, and just deleted the fat32 win partition and created a boot, swap and root partition to install ubuntu on.

---

### Post by lael on 2010-12-13
I don't know how to make Grub boot OSX, I've always installed rEFIt.  Let us know what you find.

---

### Post by arabis on 2010-12-14
Where did you put grub: on /dev/sda or on /dev/sda3? Did you erase your EFI fat32 partition on /dev/sda1?

---

### Post by yugnip on 2010-12-18
Grub is on the mbr which was created for linux/windows, and mac cannot boot there. Either use the 'option' key when booting, or install rEFIt, which will boot mac from EFI.

---

