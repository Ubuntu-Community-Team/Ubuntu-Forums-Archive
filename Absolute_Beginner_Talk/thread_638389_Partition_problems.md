---
title: "Partition problems"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Griffongob on 2007-12-12
hello all I believe a few months ago I made a post about a problem I had with mounting my windows partition onto ubuntu yet recently and for no reason at all ubuntu stopped recognizing the windows partition. I went back into the forums and found my old thread and tried following the instructions there again but to no avail. Can someone help me mount this partition? thanks!

---

### Post by Griffongob on 2007-12-12
oh and when I type: sudo fdisk -l, i get:

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *         574       33787   266791455    7  HPFS/NTFS
/dev/hdb2               1         573     4602591    b  W95 FAT32
/dev/hdb3           33788       38670    39222697+  83  Linux
/dev/hdb4           38671       38913     1951897+   5  Extended
/dev/hdb5           38671       38913     1951866   82  Linux swap / Solari

---

### Post by Griffongob on 2007-12-12
bump

---

### Post by JillSwift on 2007-12-12
It's set up in /etc/fstab, yes?

what happens when you```
sudo mount -a
```

---

### Post by Griffongob on 2007-12-12
it gives me the error:

Failed to mount '/dev/hdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hdb1 /media/games -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hdb1 /media/games ntfs-3g defaults,force 0 0

---

### Post by JillSwift on 2007-12-12
Bad dismount somewhere along the line.

Just boot Windows, it'll fix it for you. When you boot back to Ubuntu it should come back from the grave. =^_^=

---

### Post by Griffongob on 2007-12-12
i believe I may have tried that before with no effect but i will try it again

---

### Post by JillSwift on 2007-12-12
If it's still not mounting, you may want to have Windows run a full chkdsk on it, including a surface scan.

---

### Post by Griffongob on 2007-12-12
how do I do that?

---

### Post by dhruva023 on 2007-12-12
right click on drive c: (what ever you have windows on), click on the next tab.( whick will have three option -- check disk for error,  -- defrage disk -- etc..

choose the first one( check disk for error , something like that.)

clik on all the option.  and then click start.  
it will says that you have to reebot.
then just rebbot windows again,

---

### Post by Griffongob on 2007-12-12
wow what an odd thing...so while typing out my next reply I went into ntfs-config and tried using it for about the 26th time and then decided to just delete all almost all the files in my /media file and start over fresh and restarted ubuntu and magically it worked..this just boggles my mind haha

---

### Post by JillSwift on 2007-12-12
Using Windows;

Open the "My Computer" icon.
Right-click the disk in question, from the menu select "Properties".
Go to the "Tools" tab, click the button "Check now...".
Select check-boxes for "Automatically fix file system errors." and "Scan for and attempt recovery of bad sectors". Click the "Start" button in that dialog.

As it's your boot partition, it should say it can't do it right then, and request permission to do a boot-time scan of the drive. Click "Yes". Reboot, going straight back to Windows.

It'll do its thing (this may take quite a while depending on the size of your disk and how full it is) and then reboot automatically. (Wow, does MS love to reboot or what?)

Hopefully it'll catch whatever it is that is making the "open for use" flag stay on.

---

