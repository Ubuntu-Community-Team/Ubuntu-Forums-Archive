---
title: "How To Recover Ubuntu"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by damansandhu on 2007-11-14
hi , i was using ubuntu 7.04 , then i installed windows xp on a separate drive , now windows xp starts by default , is there any way to recover ubuntu without reinstalling it .

---

### Post by mikewhatever on 2007-11-14
You'll have to reinstall grub boot loader
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29)

---

### Post by bumanie on 2007-11-14
Welcome. What you have managed to do is wipe ubuntu's grub bootloader. Unfortunately, M$ don't respect that other OS's are in existence. Therefore, if you install windoze following ubuntu, windoze  very kindly overwrites grub with its mbr. What you need to do is boot up into the ubuntu live cd.  Once completed, you need to go terminal and type the following without quote marks

'sudo grub' --> enter This gets you into the grub shell. 
grub > '/boot/grub/stage1' --> enter This will provide an out put of (hd?,?) You must take note of the two numbers after hd and also make sure you put a comma between them in the next step. 

grub > 'root (hd?,?)' inserting the numbers from the last step where the question marks are.  --> enter

grub > 'setup (hd?)' again with question mark corresponds to the number immediately after the (hd). You don't need the second number. --> enter

grub > 'quit'

All going to plan grub should be reinstalled. Hope this is clear.

---

### Post by damansandhu on 2007-11-21
i did as per above method , now i god grub loader back , but when i cleck on ubuntu option it says "unable to mount from drive" something like this.

---

### Post by damansandhu on 2007-11-21
help plz

---

### Post by damansandhu on 2007-11-21
helllllp

---

### Post by pcostanza on 2007-11-21
I'm a complete newb but I can tell you that I've used EasyBCD and it was helpful to me.
Worth a shot.
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by damansandhu on 2007-11-21
lol , bcd is not runnung

---

### Post by Computer Guru on 2007-11-23
Don't keep bumping your thread, it's not cool.
 
Instructions on reinstalling GRUB: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by namanbagga on 2007-11-23
Reinstall GRUB.[This]("http://www.namanb.com/2007/11/when-computers-dont-boot.html") explains how to do so.:popcorn:

---

### Post by ugm6hr on 2007-11-23
> **Computer Guru said:**
> 
 
Instructions on reinstalling GRUB: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

He's got XP - does EasyBCD work for XP?

---

