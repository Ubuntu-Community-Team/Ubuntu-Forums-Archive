---
title: "how to install the ubuntu?thank you!"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by tcb3210 on 2007-07-24
hello!
I am a  new to  ubuntu, It's my first time to use linux.
when i run the windows base installer ,I choose the c partition to install(it has WinXP already) ,then the Pc reboot ,and i enter the ubuntu , I only find some odd characters like "<> " then I just press the enter key  and it notice me that the installation failed and i can reinstall it from the main menu.and there lists many options ,however i know nothing about it,can some one help me .
another Q:
do I need to  format my disk as linux ext2 to install the ubuntu?
thank you !

---

### Post by Foxmike on 2007-07-24
To your second question: there is many file-systems out there but ext2fs is the most used I think.  I would therefore suggest you to use it.  If you want journalling capabilities, I would tell you to use ext3fs which is the same than ext2fs + journalling.
 
Now, for the install, I never tried the Windows based install.  I have heard about it but never gave it a try for it was still beta.   I would strongly suggest you to use the official live cd.  You can download it here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
 
It will boot up the PC into a full running Ubuntu.  On the desktop, there will be an icon to the installer.  Just follow the steps, it's quite easy!
 
And welcome!:)

---

### Post by hyper_ch on 2007-07-24
And before you're going to install Ubuntu do this: BACKUP OF YOUR IMPORTANT DATA FILES

Even if you are a pro there's always a chance of something going terribly wrong and you'll be glad to have backups then.

The other thing is that I recommend to partition or rather unpartition the diskspace to be used by ubuntu before you want to install it... it makes life just easier.

---

### Post by mlentink on 2007-07-24
> **tcb3210 said:**
> when i run the windows base installer ,I choose the c partition to install(it has WinXP already)...do I need to  format my disk as linux ext2 to install the ubuntu?
thank you !
Does this mean you're using Wubi? From [this site]("http://wubi-installer.org/")?

If so, you should not partition anything, as Wubi creates its own virtual disk to install Ubuntu in. That makes it easy to unistall as well. I have used Wubi before as my second attempt at linux and had favorable results. Now I obviously run Ubuntu as the only OS on my desktop.

---

