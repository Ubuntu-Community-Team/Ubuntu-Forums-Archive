---
title: "Accidently deleted the system accounts like root , www-data...."
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by kurian on 2006-09-09
Hi, 
 Iam a new user of kubuntu ...recently i accidently deleted the system accounts like root,www-data etc. Now iam unable to log into my kubuntu..........


kindly give a good solution to recover from this problem..........


I do have a kubuntu live cd with me......

---

### Post by Miademora on 2006-09-09
How did you delete them? Manually or wich did program did you use?

---

### Post by kurian on 2006-09-10
I manually deleted them through the system settings using the administrative privilage.......


please help me.......

---

### Post by Loffe_ on 2006-09-10
Never work as root if you do not know exactly what you are doing!!! Obviously you didn't.

The easiest way may be to just reinstall your system from scratch.

//Loffe

---

### Post by whizbaby on 2006-09-10
Man. You did it. Suppose you like smoking near to gas stations, too? Only thing I can think of is

If you have valuable data on the HD:
-recover it using the live CD (e.g. burning it on CDs or copying it to another drive) 
-is there a *repair* option in the boot menu of the live CD? Try using this first.
-if there's no other option do a new install **without formatting any drives**! (you will have to accept the current partition table (select *edit manually* and don't change anything) and after that uncheck all boxes in the formatting dialogue) Do not create the same user that you created last time (that means: don't use the username of your first installation when you are asked to give new username and password during install)
With a bit of luck your data still exists in your old homedir.(your old user will not, a little tricking will be needed here)

If you don't have valuable data do a clean re-install (with formatting).

---

### Post by SkyNet2029 on 2006-09-10
> Never work as root if you do not know exactly what you are doing!!! Obviously you didn't.

Exactly. Although, since I needed to take a walk anyway, technically it should be possible to use the livecd as your booting media and mount the current partition as read/write, say in /mnt/oops. From there you would still have data access to whatever it is you need to save. Burn your files to a cd/dvd and move on. 
I am curious though (maybe just as an afterthought/project), if it would be possible to treat the existing installation as a failed chroot install and rebuilding the system users from that standpoint, say by booting from the livecd,mounting the (Foo)buntu partition and then doing a 
$chroot /mnt/oops  ....
my thinking there is in that line in 'visudo' (default settings in Kubuntu, I mean) 'Members of the admin group may gain Administrative priveleges'.. but minus the root account, that could be so much more work than it is probably worth.This is more than likely not the direction you would want to take.
Anyways... use the livecd to boot, then burn your files you want to keep to a cd/dvd so if the reinstall (WITHOUT formatting the existing directories!) fails (which it should not) you at least have your files.
I have to admit I did find this rather a humorous post. Odd, but humorous.
Good Luck.  ](*,)

---

