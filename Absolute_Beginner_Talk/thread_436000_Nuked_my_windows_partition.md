---
title: "Nuked my windows partition"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by robbie carrobie on 2007-05-07
Hi everyone, did a complete installation on my Compaq R4000, and partitioned the whole of my hdd, 100gb.  I know what a slap head however, can anyone help me to partition my hard drive so that i can run both feisty and xp.  I have read many threads that explain how it is done if a windows partition already exists, but not many when it has been nuked, some information about the ratios would be helpful, as to the actual process - kind regards Robert.

---

### Post by LaRoza on 2007-05-07
If you wiped Windows or never had it to begin with, you'll need to reinstall it. 

The easiest way would be two start over and overwrite Ubuntu and then reinstall Ubuntu.

Exactly how you partition your hard drive is up to you, but you'll need to have one partition for Windows, probably with NTFS.

You can then use the install disk for Ubuntu to resize the Windows partition and create a new one for Ubuntu.

---

### Post by Cypher on 2007-05-07
Re-install XP and give it about 25G's, or more depending on what you're going to use it for. Leave the remaining 75G unpartitioned. Then install Ubuntu and make partitions in that 75G and allow it to install GRUB on the MBR, now when you reboot you'll have dual-boot..

---

### Post by notwen on 2007-05-07
Easiest thing to do if you're not picky about your linux partition setup is install WinXP, then go back and run the Ubuntu LiveCD.  Install it and when you get to the point asking about partition, select Resize and use the most continuous free space.  While you're resizing your windows partition pay attention to how much room you leave Windows in case you may want to add more stuff to the windows side later on.  Good luck. =]

---

### Post by robbie carrobie on 2007-05-07
guys the problem is how do i actually reinstall xp, when i put the xp disk into the machine and boot up, Ubuntu runs perfectly, however it is as if the cd rom does not pick up the xp instillation disk at the beginning of boot up only after Ubuntu has loaded, i really appreciate your help and patience- kind regards Robert.

---

### Post by croxi on 2007-05-07
Does your boot sequence specify CD first? if not then that might be half your problem. You need to tell your PC that you're happy with UBUNTU but want to install XP aswell, obviously, so the way to do it is make your PC see the CD first so that you can get your XP back up and running.

---

### Post by robbie carrobie on 2007-05-07
yeah my boot sequence does specify that the cd rom should boot first in the sequence, any ideas after this? - kind regards Robert.

---

### Post by patnshan on 2007-05-07
I have read on the forums that some people's old PC BIOS' do not work well booting from CD unless you make the CD drive the only option.  I would modify your bios to boot only from CD (turn off the HD option) and then try.  Of course, once you are done you will need to go in and change it again. 

Pat

---

### Post by robbie carrobie on 2007-05-07
thanks but my bios is not that old, i think my laptop was first introduced 2005, however will give it a try anyway - kind regards robert

---

