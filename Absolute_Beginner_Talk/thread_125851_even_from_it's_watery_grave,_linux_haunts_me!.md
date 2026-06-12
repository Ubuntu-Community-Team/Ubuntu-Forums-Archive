---
title: "even from it's watery grave, linux haunts me!"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by diggs on 2006-02-05
well, not so much me as my computer.

It won't boot up ever since I deleted the ubuntu partition and then formatted it, I just get a grub error, 17 or something. a lil help, please? Thanks:KS

---

### Post by deadgoon on 2006-02-05
If you have a Windows 98 boot floppy you can boot to it and type 'fdisk /mbr' at the a:\ prompt (don't use the quotes).  This should reformat the Master Boot Record on your drive so that it will boot Windows.

If you don't have the Windows boot floppy, check Google for fixing the Master Boot Record and there should be other ways to do it.  This was just the easiest.

---

### Post by qwazert on 2006-02-05
Check out ***Bootdisk.com*** if you don't have one. They have hundreds of GREAT programs there!

---

### Post by diggs on 2006-02-05
is there anyway I can use the live or install CDs?

---

### Post by deadgoon on 2006-02-05
If you have the Windows XP install CD you can boot to it and go to the Recovery Console.  Type 'fixmbr' at the prompt.  Not sure if there is a way using the Ubuntu discs.  I did find a link I listed below.  Be sure to read all the comments.

[http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/](http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/)

---

### Post by diggs on 2006-02-05
thanks, the XP disk trick worked. learn something new everyday!

---

