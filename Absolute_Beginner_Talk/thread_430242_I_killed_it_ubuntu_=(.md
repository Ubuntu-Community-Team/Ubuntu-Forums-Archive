---
title: "I killed it ubuntu =("
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by bethaviv on 2007-05-01
Ok... in an attempt to try to get my mouse buttons working properly, I killed xorg-conf...

I backed up the file and wrote down the instructions in case I fudged up (which I did). Now I'm loaded into the Live CD, but I don't know how to access my files to fix them. I guess I'm saying I don't know how to mount the drives in Live CD and login to my account so I can mv the files.

The guide said that if it failed, I'd be at a prompt, but even though I was able to type the commands, it didn't work.

Thanks =D

---

### Post by starcraft.man on 2007-05-01
You don't actually need to boot into the live cd, if you take the CD out and reboot Ubuntu will let you log into a command line version of itself. Just type your username and password. Then you'll have terminal access, then you just need to copy over your backup to your old xorg.conf file. 

Easy enough, hope that works. :)

---

### Post by tact on 2007-05-01
Ok so you fudged up xorg.conf.  But you can still boot right?   You got a few options before reverting to booting off the liveCD..

1.  Can you boot normally then when it all turns to custard ALT-F1 to get to a console?   If so then you got a chance there to log in as yourself and use sudo to copy back the backup.   

If you keep getting interrupted by GDM trying to fire up you can stop it for a while with 
sudo /etc/init.d/X11/gdm stop

2.  If you cannot boot at all normally and get to a console - can you press "esc" as soon as you see the grub notice on screen?   If so then you can then select to boot the other recovery kernel thats provided.

3.  all else fails then you can boot liveCD and mount the HDD partitions as you are suggesting:
you can use a terminal and do it manually or...
open gparted and use it to mount the partition you want to access.

You might have to create a mount point before using gparted so use terminal and 
```
sudo mkdir /media/fudged
```

then use gparted to mount ht epartition to the directory you created

---

### Post by Nythain on 2007-05-01
and since no one has mentioned how to copy a file at command line, it would be a simple sudo cp /path/to/your/back/up/xorg.conf /etc/X11/xorg.conf

---

### Post by bethaviv on 2007-05-02
Tact - #2 worked for me.

If I let Ubuntu keep loading it would ask if I wanted to see the error to check it. And then I'd end up at ">" and anything I typed didn't do anything.

I knew there *had* to be a repair mode ( a la "safe mode" or "recovery console"...), but couldn't figure it out until you said to press Esc at the GRUB menu.

Duh... I was just confused because the guide said if it failed I'd be at a cmd line and i freaked out because Ubuntu wasn't booting =(

i talked to my boyfriend and he was just like "mount the drives." so we spent a lot of time looking up how to mount a drive. Then i decided to post here because nothing we were doing was working =(

Luckily, the GRUB menu saved me, thanks tank =)

So yeah.. I'm back into Ubuntu (yay!). My time interval between posting and right now was due to going to RJ's (bar and lounge) with some friends before i decided to take the hammer to my computer. (Which I would never do...)

Thanks again =)

---

