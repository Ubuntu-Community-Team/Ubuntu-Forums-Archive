---
title: "Where has my windows entry gone?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by miggols99 on 2007-04-13
I recently installed some updates and then restarted. When I got to where I choose which OS I use, windows XP was gone! How do I bring it back?

---

### Post by miggols99 on 2007-04-13
I've fixed this now. I added the entry manually. :)

---

### Post by Herman on 2007-04-13
If you have added it somewhere *outside* *of *the debian automagic kernels list it will be safely copied to your new menu.lst when your menu.lst is refreshed by update-grub during your next Ubuntu kernel update.

If you have pasted it anywhere *inside* your debian automagic kernels list it will be automagically deleted each time you are given a new kernel in Ubuntu, which would be quite annoying after a while.

The beginning and end of your debian automagic kernels list in your menu.lst file is clearly marked, but it's an extremely frequent occurrence for Windows users to fail to read what is printed in the file for their guidance, and then blame grub or Ubuntu for their suffering. :D

We all hope new users will like Ubuntu and want to keep it and maybe eventually even convert  to using Ubuntu only. Therefore most of us would like you to be as comfortable as possible while you are making your transition.
I hope I have helped.

Regards, Herman :D

---

### Post by difylos on 2007-04-13
For me too.
How can i fix it;
How can i add the entry manual ?
My windows parition is in D:/

---

### Post by miggols99 on 2007-04-13
Ok here's what I added:
```
title		Microsoft Windows XP Home Edition
root		(hd0,1)
makeactive
chainloader	+1
```
You may need to change "root"

You add it to the /boot/grub/menu.lst file near the bottom. Remember to backup!

---

### Post by Herman on 2007-04-13
That's right, you can add it either above or below the debian automagic kernels list, that is, either at the bottom or up around the middle of the menu.lst file.
Click on my third sig link for more details.

Regards, Herman :D

---

### Post by difylos on 2007-04-13
Thanks its working now :D 
Love from Crete Greece  !

---

### Post by Herman on 2007-04-16
:wink:

---

### Post by heartbeat on 2007-05-17
Windows won't boot.

It says Starting up and won't boot any further

---

### Post by Herman on 2007-05-17
Hello heartbeat,
Does this happen after Grub has already done it's part of the job and has successfully chainloaded Windows, (handed over control to Windows NTLDR)?
I am guessing that's what you mean, so fixing Grub won't help, Grub is already working okay, the problem is in Windows.

What partition number was Windows before you repartitioned your hard disk and what partition number is it now? (I mean number, like 'hda1' or 'hard disk 1, partition 1 or so, partition letters like 'drive C' are meaningless when you start dual booting). Can you do 'sudo fdisk -lu' in a terminal in Ubuntu and post the output here please?

Probably, (if I'm guessing right), all you will need to do is edit your boot.ini in Windows, or maybe fix Windows boot sector. (Although I don't know why your Windows boot sector could be affected, because neither Ubuntu nor Grub will touch that unless forced to).  
In the meantime, the best way for you to boot Windows for now, without even fixing it, would be to go to this website, [http://tinyempire.com/notes/ntldr]("http://tinyempire.com/notes/ntldrismissing.htm")
(even if your exact error is not 'ntldr is missing'. That site is good for many Windows booting errors. You should download an NTLDR CD from there. (Or a floppy disk if you prefer). You will be able to boot Windows with that for now. If you can't, let me know.
Once you can boot Windows, you should be able to fix Windows from within Windows itself.
Let me know how you get along, I'll be watching this thread.

Regards, Herman :)

---

