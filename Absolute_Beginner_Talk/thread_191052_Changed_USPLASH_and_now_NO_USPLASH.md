---
title: "Changed USPLASH and now NO USPLASH"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by carl13 on 2006-06-07
Not sure what is going on here but I tried to change my usplash according to:

[This HowTo]("http://www.ubuntuforums.org/showthread.php?t=82835&highlight=usplash").

Basically, I just followed it line by line. Apart from copying and moving files, I really did not understand what I was doing. 

Anyway, now when I restart or boot, my screen is black.

Any ideas of how to trouble shoot this?

---

### Post by Dice on 2006-06-07
I went through the same exact thing you are going through.  It turns out, you need to add to a line in /root/grub/menu.lst. The line will be the one which boots Ubuntu.

Mine looks like this: /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash _vga=789_

The part that needs to be added is underlined as above.  This changes your monitor's resolution allowing the splash to be shown.

```
sudo gedit /boot/grub/menu.lst
``` (In case you wanted the command:-D )

---

### Post by carl13 on 2006-06-07
thanks for the reply
i tried adding the line but still no luck

do you care to post your "menu.lst" file
maybe if i see a working one, then i can figure out what is wrong with mine

---

### Post by catlett on 2006-06-07
Did you make a backup of your grub menu.lst before you changed it? 

As for the how to I think you had to enter some information specific to your system in the last command . I would post to that how to thread about your error. Most likely the originator is subscribed to the thread and will notice your post. If anyone will know what to do it's him.
If you just want grub back and you don't have a backup you can try re-installing grub or updating grub and see if it changes the configuration. It might not because it usually just looks for new kernels on an update. Also, when it reinstalls,  if the paths are right it doesn't change anything. You might get lucky.

These to commands install and update grub. This is specific to an ide hard drive. ```
sudo grub-install /dev/hda
``````
 sudo update-grub
``` If that didn't work I would post a reply to the how to thread.  Good luck.

---

### Post by carl13 on 2006-06-08
thanks for the help, I did make a back up, maybe I should restore the original file and start over

---

