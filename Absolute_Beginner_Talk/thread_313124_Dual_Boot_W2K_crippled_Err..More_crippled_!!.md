---
title: "Dual Boot W2K crippled Err..More crippled !!"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by mnduck on 2006-12-05
Hi.

I'm dual booting Ubuntu and W2K, linux is on the primary slave a different physical disk from W2k.

Unfortunately windows is just about crippled, any thing that involves disk access to anything other than C: causes MASSIVE hold up's. Even starting control panel, computer management, disk storage will bring the PC to a halt.  I believe that there is some sort of conflict occurring windows don't wana share :evil: 

I need to know:-

How to sort it out

or 

How to remove GRUB (I'll then just reformat over Linux to FAT32) A little searching and it looks like fdisk/mbr should do the trick.


Regards and thanks      mnduck

---

### Post by mnduck on 2006-12-05
No Help then?? 

If I can not resolve this I'll have to bin Linux :( :(

mnduck

---

### Post by devnulljp on 2006-12-05
Don't fdisk /mbr on win2k. Install the Recovery Console and fix it from in there.

Winnt32.exe /cmdcons

I think you want fixmbr but check the command (use ? in the console)

No idea wht's causing the holdups, I've been dual-booting for years w/ win2k and various linuxes with no problems of the sort you mention.

---

### Post by bodhi.zazen on 2006-12-05
The best way to fix your Windows problems is to delete the partition :p

I have no idea what the problem may be, but I am certain that neither Ubuntu or grub is the source. Look within windows.

Best of luck.

---

### Post by mnduck on 2006-12-05
I really think W2k is trying and failing to read EXT3, I've removed the drive letters in windows but it's still trying maybe because I still have a Fat32 partition on that drive.

I'll keep trying.


Thanks        MNDuck

---

