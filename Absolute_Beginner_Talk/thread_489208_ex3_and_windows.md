---
title: "ex3 and windows"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by lordspidey on 2007-07-01
alright now i have Ubuntu and windows on two different hard drives but i cannot accesses all the files in my ex3 formatted drive from windows Xp

another little trouble i have is i cannot dual boot i get no option to boot into ubuntu only windows 
i tried booting from the Ubuntu drive but with no successes 

thank you in advance 

WoOOooOhooooOOO for Ubuntu
[img]http://static.filefront.com/images/personal/l/lordspidey/78836/xnwvdsbnva.jpg[/img][img]http://static.filefront.com/images/personal/l/lordspidey/78836/lvzsgpvovx.jpg[/img]

---

### Post by logos34 on 2007-07-01
get **fs-driver** for windows.  it will give you read + write access to ext3 filesystem.

Did you perhaps install windows after ubuntu?  It could have overwritten the grub bootloader.  Grub does not necessarily install on the ubuntu disk (it goes to whatever drive is listed first in the bios boot priority.)

---

### Post by lordspidey on 2007-07-01
ok great i can access all of my ex3 partition but i still cannot boot in Ubuntu i tried booting from hdd1 (the one with Ubuntu on it) and i did not get anywhere i just started up normally into windows

---

### Post by logos34 on 2007-07-01
> another little trouble i have is i cannot dual boot i get no option to boot into ubuntu only windows
i tried booting from the Ubuntu drive but with no successes 
...
i still cannot boot in Ubuntu i tried booting from hdd1 (the one with Ubuntu on it) and i did not get anywhere i just started up normally into windows

From the sparse info you've provided I'm guessing that grub either installed on the MBR (master boot record) of the other drive and was overwritten by a subsequent windows install, or it did not get written to the mbr at all, OR it is on the ubuntu drive but for some reason is defaulting to windows, the hidden option is enabled and the timeout is zero (meaning you won't even see the menu come up).

When you set the bios to boot hdd, the ubuntu drive, do you see 'Grub loading...' flash by on the screen?  If so tap the 'Esc' key to bring up the grub menu, then select ubuntu.  

If not, then it's not there, in which case the easiest thing to do would be to try reinstalling grub to the ubuntu drive.

To do that boot from the ubuntu live cd and load the desktop.  Open a terminal and type:

[B]sudo grub

find /bootgrub/stage1[/B]
[enter the output 'hdx,y) in the next command]
[B]root (hdx,y)
setup (hdx)
quit[/B]

This should put grub on the mbr of the ubuntu drive and allow you to boot from that.  There may even be a windows entry that will work.  Post back with the results.

---

