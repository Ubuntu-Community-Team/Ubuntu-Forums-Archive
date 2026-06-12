---
title: "Kernel Panic dpkg --configure -a Woes ... HELP?!?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by TBayCrusher on 2007-04-25
..... Anyway
I'm Tired Of Every Flash Video I Try To Watch Not Loading 
They All Say, Must Upgrade To Latest Flash Version Blah Blah 
So, Flash, Everyone Has Flash, Shouldn't Be Hard Right??? That Was My Hope
So I Go To The Site About How To Install, It Gives What (To Me) Were Two Totally Confusing Install Ideas 
I Tried, Say, 25 Times To Do What They Suggested, Still No Flash 
Fearing A Mistake I Try Automatix, Scan For Flash, Find It & Start The Process
It Goes Wacko & Starts Flashing & Crashing & Prompts Me....
That I'll Need To Go Somewhere (Root Terminal?) & Type In dpkg --configure -a
The Package Manager Tells Me To Do Likewise 
So I Go To A Terminal & Do This & That Kills The Whole Box On Restart 

Anyway, Now When I Try To Restart I Get.....

Booting 'Ubuntu, kernel 2.6.15-28-686'
root (hd0,0)
Filesystem type is ext2fs, partition type 0,83
kernel /vmlinuz-2.6.15-28-686 root=/dev/hda2 ro quiet splash
[Linux-bzimage, setup=0x1c00,size=0x170561]
initrd /initrd.img-2.6.15-28-686
[Linux-intrid @ 0x1fcfc000, 0x2e4000 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
[17179572.532000] RAMDISK: ran out of compressed data
[17179572.532000] invalid compressed format (err=1)
[17179572.532000]  Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)
[17179572.532000] 

That's All I Get, I Cannot Seem To Get Past This Black Screen Of Death To Fix This
None OF The Posts ON This Problem That I've Read Here Address This, 
But With So Many Having This Same Problem, I Could've Easily Missed The Necessary Tip

---

### Post by markoloka on 2007-06-09
Can you start on older kernel? Latest kernel did that problem to me. It seems kernel update got corrupted as there was error on adept.
On terminal try sudo apt-get update   if it says to do... dpkg... do it.

---

