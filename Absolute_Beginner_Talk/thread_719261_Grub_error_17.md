---
title: "Grub error 17"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by CidBahamut on 2008-03-09
So I was transferring some files to my external harddrive tonight when things went haywire. As far as I could tell my machine locked up so I did a manual shutdown. 

I reboot, but instead of getting back into Dapper Drake, I get stuck in a terminal screen with the words: 'Boot halt- system failure'. 
Swapped out the harddrive and got something up and running. Figured it was the connection and went back to the original harddrive.

This time grub loads and stops telling me "error 17".

What do I do now?

---

### Post by mikeyphi on 2008-03-09
Looks like a problem with the Grub bootloader- normally in the first disk section and then in your /boot/grub/menu.lst

Could be that the glitch caused a disk error. You will need to use a LiveCD or a Grub CD to reload Grub.

---

### Post by oliviacond on 2008-03-09
this might help
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)
[http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9)

---

