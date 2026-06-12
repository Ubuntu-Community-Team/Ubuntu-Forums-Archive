---
title: "Dev/sda2 has gone 49710 days without check..."
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by markoloka on 2007-09-09
I have 6 months old Sata2 hdd and i'm using Kubuntu 7.04 and w/ dual boot XP (were i'm writing this). 
Kubuntu won't start anymore and it says on start: /dev/sda2/ has gone 49710 days without check. 
How can i've been using this kubuntu for 136+ YEARS without check. Someone explain to me. 
Pc check and hd's manufacturers test says hdd is ok.

---

### Post by lisati on 2007-09-09
It is normal for Ubuntu and other *nix systems to check the sanity of its disks every so often until you tell them not to. Are you able to restart and run Kubuntu?

EDIT: Sometimes the first time the check is done it comes up with a "strange" number.

---

### Post by markoloka on 2007-09-09
No i can't run kubuntu. All fonts are totally messed (look like spades and on son rather than actual letters) and graphics don't work. 
It just checked system few days ago but now it's saying that it hasn't checked in 49710 days. System clock in bios is fine and also in xp. Luckily i have dual boot otherwise i would be really f****d.

---

### Post by zero-9376 on 2007-09-09
does the check fail? if the automatic check fails then it asks you to check the fs manually, if you dont do this it may not mount the partition and you may experience problems

EDIT: on another note, this 'bug' with the days should be addressed as it clearly causes confusion, also makes the OS look bad

---

### Post by EnglishRob on 2007-10-05
I've just seen this on a fresh install of Ubuntu 7.04 on my dad's IBM ThinkPad r50e with a brand new 120GB Seagate hard drive.

The install seems to go though fine, boots up okay and then I update the system.

After the reboot it runs fsck saying that it's been around 49180 days since the last disk check.  It goes through and reboots and then does exactly the same thing.  I've reinstalled Ubuntu twice and it did it on both occasions after a reboot.

I'm going to give Ubuntu 7.10 Beta a try, touch wood that'll be okay (I'm installing 7.10 Beta because my dad needs his laptop working for tomorrow when he goes away for a week - I can install the final version of 7.10 when he's back).

Rob

---

### Post by Ripfox on 2007-10-05
Wow cool of your dad to let you Ubuntu his laptop.

---

