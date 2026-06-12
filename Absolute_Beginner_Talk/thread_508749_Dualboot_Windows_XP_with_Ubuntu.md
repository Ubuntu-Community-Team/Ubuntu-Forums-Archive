---
title: "Dualboot Windows XP with Ubuntu"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Flamespectre on 2007-07-24
Hi all, I installed XP after Ubuntu and got grub replaced, I managed to restore grub but now I can't boot XP. I know there is similar threads but they haven't helped much. I found this to add in grub:

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

But will it work even if my XP partition is on hda2? And how do I change grub?

---

### Post by wolfen69 on 2007-07-24
if you have seperate hard drives, i recommend physically disconnecting 1 hard drive while installing an OS. that way they wont even know each other exist during install. and hence, no boot problems. you can choose which OS to boot via BIOS. i do this myself. ive never been a fan of dual booting on same hard drive.

edit: you could insert xp cd, boot, choose recovery console, and type: fixmbr

---

### Post by Jose Catre-Vandis on 2007-07-24
Should work

In grubspeak hd0 = hda, therefore

hd1 = hdb

To add it to your grub menu.lst

```
sudo gedit /boot/grub/menu.lst
```

Scroll down until you get to the bottom of the file
Paste your text in there
Save & Close
Reboot

Press ESC if you have to to get the boot loader menu, and arrow down to get your Windows

---

### Post by Flamespectre on 2007-07-24
Both partitions are on the same drive so that won't work, also, grub is installed on the windows partition so I can't switch by changing the boot flags.

---

### Post by Orochi on 2007-07-24
GRUB isn't installed to a partition, it's installed to the drive's MBR.

Use this code:

```

title Windows
root (hd0,0)
makeactive
chainloader +1

```

Except instead of (hd0,0) subsititute in the correct partition and drive numbers. It's hd*x*,*y* where x is the drive number (you only have one drive I believe so it should be drive 0) and y is the parition number (most likely either 0 is Ubuntu and 1 is XP or vice versa depending on the physical order of the partitions on your drive).

Since you only have one drive you dont need to worry about drive mapping.

Also when you're looking at grub's menu.lst there shoud be lots of example code in there that's commented out. There should be example code for Windows, you can look at it to make sure what you're doing looks right. Most of the options in menu.lst are explained pretty well in the comments of the file, so if you read through it you shouldn't have a problem.

---

### Post by Flamespectre on 2007-07-24
Thanks alot guys, works perfectly. :)

---

### Post by Jose Catre-Vandis on 2007-07-24
Sorry I misread you had Xp installed on a seperate drive. Glad you got it going :)

---

### Post by PsychedelicWonders on 2007-07-25
Isn't installing XP first a better idea?

---

### Post by Orochi on 2007-07-25
It doesn't really matter which way you do it. If you install XP first, then when you install Ubuntu it will configure GRUB automatically for you. If you install it second it just means you need to setup GRUB yourself.

---

### Post by OZTack on 2007-07-31
> **Orochi said:**
> It doesn't really matter which way you do it. If you install XP first, then when you install Ubuntu it will configure GRUB automatically for you. If you install it second it just means you need to setup GRUB yourself.

Sorry to bring up an old thread :-)

I JUST installed Feisty on a WIN XP machine.
I installed to empty space on a secondary drive , with WIN XP booting from partion 1 on the primary drive.

Interestingly........ Grub MISSED out my XP installatiion all-together :(  I Only had standard, recovery and mem test available at boot.:confused:

I added the lines suggested to the VERY end of the menu.lst file

```


title Windows
root (hd0,1)      <-----0,1 in my case......
makeactive
chainloader +1


```

and it works beautifully :)

However - I am surprised it didn't do that automatically? Anyone have any ideas why?

Anyway - working now :)

---

