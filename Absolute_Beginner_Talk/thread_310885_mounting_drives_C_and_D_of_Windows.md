---
title: "mounting drives C and D of Windows"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by cc28271 on 2006-12-02
when one boots using a knoppix live CD, the icons of the windows hard drives appear on the screen and they have to be double-clicked to mount them. 

but, when one boots using a ubuntu 6 live CD, no icons are present on the desktop. how can one mount the windows partitions? what is the simplest way to mount drives C and D of windows?

---

### Post by igknighted on 2006-12-02
During the install you can specify a mount point and they should be automatically mounted on bootup, otherwise I believe it requires some editing of the fstab file, although I am not sure of the exact method.  Search the forums, I know there are many guides for this.

---

### Post by agustin.g on 2006-12-02
in Dapper (6.06) there is a "Disks" application in the System --> Administraion menu, all you have to do is specify the mount point (where you want the C and D drives to be) and click on "enable" button. However i am not sure if it will work on a liveCD

---

### Post by Dmole on 2006-12-02
cc28271,

agustin.g is correct you can use the "Disks" application on the liveCD.

but you will not be able to use the partition management tool on mounted volumes.

---

