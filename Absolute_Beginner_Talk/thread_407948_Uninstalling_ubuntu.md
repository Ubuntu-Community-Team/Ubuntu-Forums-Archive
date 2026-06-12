---
title: "Uninstalling ubuntu"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by ekom on 2007-04-12
After playing around with ubuntu I decided that i would like to uninstall it from my machine.  Many programs i use are all Windows only programs, not to mention I get annoyed by the GRUB loader.  I read around about uninstalling GRUB and it seems the way everyone says to do it is use the recovery console.  I tryed this, but when I get to the recovery console it says it cannot locate my hard drive disk.  Im have dual boot windows xp and ubuntu.  Is there any other way that i can get my windows booter back if I'm having problems with my recovery console? or is there a way to fix this recovery console problem I have?

Thanks

---

### Post by antoz on 2007-04-12
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by elysium444 on 2007-04-12
1.Format the partitions that you created for ubuntu, format them while you are in windows with whatever software. 
2.than put windows cd in, restart, boot windows cd, than go to repair windows, then type username and pass and you will be logged in, than type "fixmbr" 

If you prefer try the second step first to get your self around than format...

---

### Post by ekom on 2007-04-12
elysium444: like i mentioned i tried doing the repair windows but it tells me that it cannot locate my hard drive

antoz: i tried the fixmbr.exe method and it failed.  I did it just like the instructions on the site said to.  I can try the super grub method but I dont quite understand how to use that.

---

### Post by antoz on 2007-04-12
I personally have only ever fixed my mbr with a floppy, the link gives lots of options. You could make a boot disk in Windows (floppy) and use that to fix it, but you have to get into the bios and change the boot sequence so it boots from A, once it boots you get a black screen with a prompt A:\ thats where you type in fdisk /mbr This should fix it and next time you boot grub will be gone and it will boot into Windows
PS: you can change the boot seqence again in the bios.
After that you can delete the Ubuntu partitions with the windows disk manager or you could even use the live Ubuntu CD to do that.
Hope this is of some help,A

---

### Post by ekom on 2007-04-12
awesome! super grub worked great, actually easier than you said... all i had to do was click windows then click fix mbr.

thanks a ton

---

