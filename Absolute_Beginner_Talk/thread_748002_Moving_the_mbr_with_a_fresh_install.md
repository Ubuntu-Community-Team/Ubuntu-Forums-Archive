---
title: "Moving the mbr with a fresh install?"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by muteXe on 2008-04-07
Morning All,
For about a year my linux partition has been on my external HD.  However because i'm a bit of an idiot when i installed linux on it, GRUB was put there as well.  So when i switch my machine on I *have* to have my external drive in, even if i want to boot into windows (which is on my internal drive in my machine), or else i get grub error 11.   It's not too much bother though I guess to have the external drive in.
My question is this really:  When Hardy is released i would ideally like to install this on my internal drive, and not use my external drive at all for linux.  If i do this, i.e. boot off the Hardy live cd and install from the desktop, will it put grub back on my main internal drive?
Sorry if this is a dumb/easy question.
Many thanks,
mute

---

### Post by darren1270 on 2008-04-07
You want to dual boot hardy and windows off internal drive?
These are the steps I would take.

1. Since your booting off external drive (Grub) I would boot from windows XP Cd...then let it go through the steps like ur going to install windows but don't  install it.. I believe if you let it go to the repair Not the first one the one that takes you to c:\  when u get there type fixmbr and then when you reboot you should boot into windows.

2. Boot from Hardy CD and then install using whatever method you want for partitioning your drive.

3. After installing and booting into Ubuntu you should be able to reconnect your external drive to pull any data you have back over to your fresh new Ubuntu.

Just my thought but should work for you.... Maybe there is an easier way that someone else will share...

Good luck!

---

### Post by muteXe on 2008-04-07
thanks for your quick respone :)
I'll burn my /home folder onto a cd, so theoretically i can format my linux partion on my external drive and use it for data.
I'll see if i can dig out my win xp cd.

Thanks again,
mute

---

### Post by ajgreeny on 2008-04-07
You should be able to do the first part of darren1270's suggestion but, then after restoring the windows MBR with the recovery module on the windows install disk, you can put grub back to wherever you want with your current ubuntu live CD.  If you chose to put it on the external disk and have that as your first boot device, grub will appear if it is connected and you will be able to chose which to boot to.  If it is not connected, the windows MBR will take over and boot you straight into windows.

As a thought, it may even be possible to do it quicker with the command from ubuntu ```
sudo grub-install /dev/*d#
```The *d# is going to need changing, obviously to whatever your external disk shows as in your system.  You will also need to ensure that the device you need is listed in the /boot/grub/device.map using the same format as the other disks listed there, but that is easy, I've always added my floppy disk that way, and keep a copy of grub on a floppy just in case.

Good luck with it, and don't worry too much, you can easily get grub back with the live CD if you should mess things up.

---

### Post by darren1270 on 2008-04-07
Hope it works out for you!

Good Luck!

Darren

---

### Post by muteXe on 2008-04-07
thanks both!
I was hoping that i would be as simple as leaving the ext. drive disconnected, reinstalling HH on the internal drive, and hoping that the isntallation process would move my mbr back to my internal drive (seeing as my Feisty installation moved it to my external drive somehow!).  Looks like it won't be that simple.
Thanks again,
mute

---

### Post by muteXe on 2008-04-07
hold on.....  could i not just move the MBR with super grub disk, rather than fixmbr from windows?
Is that possible?  I really don't know what i'm talking about here :D

---

### Post by muteXe on 2008-04-07
seems like i got lots to read on super grub. i'll let you know how it goes.
thx,
mute

---

### Post by twin_57103 on 2008-04-07
I've used Super Grub to restore a Window MBR before - could you just restore the Windows MBR, then install Hardy normally?  It was pretty painless - I had to remove the internal drive that held GRUB because it was failing and I needed to restore it so Windows would boot without it (WIN => MBR & !WIN!).  From there, I think you could do it like a normal new dual-boot.  Hope that helps!

---

### Post by muteXe on 2008-04-07
woohoo yes it does thanks twin_57103!
i'll give that a go when official hardy is released.
thanks for the help all,
mute

---

