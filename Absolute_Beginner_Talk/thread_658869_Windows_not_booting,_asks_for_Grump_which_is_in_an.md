---
title: "Windows not booting, asks for Grump which is in an external hdd!!"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by darchmitt on 2008-01-05
Hello!
I recently managed to install ubuntu 7.1 on an external hard disk. On my internal hard disk has Win XP. I had trouble first because, as i read, i believe the linux OS thought that grump was installed upon the internal (XP) disk.. however i found a post here that instructed on how to change the "place to look for" grump using ubuntu´s terminal..

Now, when i start the computer with the external hard disk it boots correctly, it even asks me for which OS to boot from (ubunty/ win XP).. however, when starting  up the computer without the external hard disk connected, a "grump loading error 21" appears.  So as i understand, the computer tries to load grump always... my question is the next:

how can i make the computer to boot win XP without asking for grump, like a normal PC when the external hard disk is not conect?
i believe, for what i´ve read, that grump has been writen over a windows XP booter or something like that... how do i restore windows booter???

well, i hope someone can help--
an a newbie,, so pleasse, advice.....
also.... i did try to look for threats like this one including the "similar" ones that the forums show before i post this one, but i didnt find one quite like mine...

thanks for "reading"

---

### Post by mikewhatever on 2008-01-05
The problem is that the initial part of GRUB is in the MBR of your internal HDD, while the main art is in /boot/grub on the external one. To fix it, you need to restore Windows boot loader, and reinstall Grub so that its initial part gets to the MBR of the external HDD. Check this thread for more info [http://ubuntuforums.org/showthread.php?t=657237](http://ubuntuforums.org/showthread.php?t=657237)

---

### Post by darchmitt on 2008-01-05
Thanks!
ill give it a try!


Hey i think i acctually managed to reinstall GRUB on the external HDD... but how do restore Windows bot loader on the internal hard disk??

---

### Post by mikewhatever on 2008-01-05
> **darchmitt said:**
> Thanks!
ill give it a try!


Hey i think i acctually managed to reinstall GRUB on the external HDD... but how do restore Windows bot loader on the internal hard disk??

Either Windows recovery console [http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console) or Super grub can do it [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download).

---

