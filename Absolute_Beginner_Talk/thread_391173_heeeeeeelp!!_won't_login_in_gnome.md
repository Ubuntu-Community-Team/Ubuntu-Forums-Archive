---
title: "heeeeeeelp!! won't login in gnome"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Morkhaar on 2007-03-22
so.. how could i describe what i've just done?
well  i' ve installed fuse 2.5.3, then fuse 2.6.0 then ntfs-3g and then followed a thread and installed the divre ntfs-config. I managed to mount my drives successfully, but wasn't able to mount my external drive. so i opened the fstab and added at the end /dev/sda1 media/sda1 ntfs-3g and so on , rebooted and after username and password the system shows only the color of the desktop and the mouse pointer (which is able to move) and nothing else! I  update via the fail safe gnome to the edgy eft (i was using the dapper drake) but the problem persists. 
Oh, i also removed some things that had to do with the gnome and evolution/nautilus applications by mistake...:mrgreen: 
does anybody know what to do??!!

i alreay returned fstab at its default state through the terminal but to no improvement. besides, shouldn't upgrading to edgy restore the fstab?

---

### Post by tcrroadie on 2007-03-22
Well, do you remember what you removed relating to Gnome?

Did your problem start after you removed packages relating to Gnome?

I would think that if you had a disk mounting problem, you would have not gotten as far as loging in and getting a partial desktop.

Can you post your fstab?

You can try reinstalling gnome. 

1.  First after loging in, press ctrl+alt+F1 to bring up the command line. 

2.  Then reinstall ubuntu-desktop

```
sudo apt-get --reinstall install ubuntu-desktop
```

You may want to what a while to see if you get any more suggestions.

---

### Post by Morkhaar on 2007-03-22
i'll try it, but these items were removed a little earlier and i had already rebooted without problems. Some things were not working nor some commands for the terminal, but nothing serious...

---

### Post by Morkhaar on 2007-03-22
thanx man!!!  didn't think it would work but apparently i had removed something rather important!! 
well, all's well that ends well! my system now works + i updated to edgy!! que suerte!!
thanx again!

---

