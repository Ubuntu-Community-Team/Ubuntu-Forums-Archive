---
title: "need help dual booting Ubuntu and windows 2000"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by indrion on 2007-05-13
ok, well i installed Ubuntu and realised that alot of the things i want\need to do is in windows, so i checked to see if i had any windows disks and i found a windows 2000 one. i have no clue on how to set up a dual boot though, im currently on a laptop and thats what i want to set it up on, however i cannot view any movies that tell how to set it up because it always says i need java or quicktime or something like that and when i'm installing in the terminal it wont work...so if anybody can help me i'd be pretty grateful.

and are dual boots free, cause if not i can get money back on my laptop as soon as something happens *cough* and get a mac and just get bootcamp...

---

### Post by Nythain on 2007-05-13
dual booting is free as long as you own a copy of windows... as far as getting it going... if you dont mind losing your current ubuntu install its cake...
install windows... leave enough free unpartitioned space for ubuntu, then install ubuntu, grub will pick up windows and all will be well

if you dont want to lose your current ubuntu install, i would suggest using gparted to free up enough unpartitioned space for windows... install windows, then use a Super Grub disk to repair grub, cause windows is more than likely going to jack it... but it might take a little manual configuration of your /boot/grub/menu.lst file after you fix grub to have both the windows and ubuntu entry... i would read up on grub and the menu.lst file before going at it so you are familiar with how it works and what to do in case anythign goes wrong... and of course, download and burn the super grub iso

---

### Post by jkblacker on 2007-05-13
It's usually best to install Windows first, because the Windows installer just isn't very intelligent. So, I'd back up all your files, make a note of which extra programs you have installed (making it easier to remember what you've got later), and do a clean install of windows. 

16 hours later, pop the livecd in and use GParted to shrink your Windows partition, add three partitions (a / one, a /home one and a swap one - what size is your hdd, and how much ram do you have?) and install, making sure to use the manually edit partition table option, and mounting the partitions as /, /home and swap (you'll need to check the 'format' box for the / partition, iirc), and you're away.

As for 'free', I don't understand what you mean. Do you mean does it void the warranty or something?

There's a good dual boot tutorial somewhere, I'll go grab the link now; can't help you with the java problem I'm afraid!

---

### Post by indrion on 2007-05-13
i have no clue what you just said lol, are you saying install windows and then ubuntu again but leave enough space for windows? and how would i switch between the two...

---

### Post by zvacet on 2007-05-13
[http://ubuntuforums.org/showthread.php?t=358183&highlight=grub]("http://ubuntuforums.org/showthread.php?t=358183&highlight=grub")

For movies look this page

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by indrion on 2007-05-13
well that threads for xp does it make a difference?

---

### Post by Nythain on 2007-05-13
nope, they should function the same, specially since xp is nothing more than a dumbed down prettier version of 2000 as far as im concerned... now if you were talking vista, that would make things much more complicated from what i gather

---

### Post by indrion on 2007-05-13
k, well i'll try it when im not half asleep lol, thanks guys

---

