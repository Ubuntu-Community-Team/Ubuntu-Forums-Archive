---
title: "Grub Will Not Reinstall"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Spaceman Spiff on 2008-01-13
Hey guys, I have spent all day trying to figure out how to reinstall my grub loader only into my MBR but it's not working with me at all.  If anyone can offer some tips, I am going to list my outputs below.  I am stuck on "setup (hd0)", I am getting "Error 22" as you will see.

Some notes,
  - I downloaded the supergrub cd and tried to fix boot for linux, it found my linux partition and I pressed enter on it, but it simply restarted and windows xp started back up which makes me to believe it didn't install grub in the mbr
  - My linux partition is just fine, in fact I managed to put into it using the supergrub cd and I am using it right now
  - My /boot in my linux partition is fine and shouldn't have changed

sudo grub ->

[INDENT]grub> find /boot/grub/stage1 
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

grub> [/INDENT]

---

### Post by dstew on 2008-01-13
It is possible that you need to run grub from a system other than the one that is on the disk you are installing on. Did you try to do the same commands from the grub prompt when booting the LiveCD, or the SuperGrub CD? I note that on my system, when using the grub shell from inside my Ubuntu system, it cannot find by /boot/grub/stage1 file. The grub shell is different than native grub, running in its own system.

---

### Post by mattismyname on 2008-01-13
I can't give you a definitive answer, but can point you to some additional reading where other people with error 22 have found solutions:

[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
[http://ubuntuforums.org/showthread.php?t=613290#post3772993](http://ubuntuforums.org/showthread.php?t=613290#post3772993)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=4047352](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=4047352)

---

### Post by Spaceman Spiff on 2008-01-13
Dstew, I will try that right now.

Mattismyname, I perused the articles you have linked but they focus on error 22 when you  have grub installld in the mbr already.  Many of them list the setup(hd0) command and have no troubleshooting for what happens if that command fails.

Thanks for the tips, much appreciated.

---

### Post by Spaceman Spiff on 2008-01-13
> **dstew said:**
> It is possible that you need to run grub from a system other than the one that is on the disk you are installing on. Did you try to do the same commands from the grub prompt when booting the LiveCD, or the SuperGrub CD? I note that on my system, when using the grub shell from inside my Ubuntu system, it cannot find by /boot/grub/stage1 file. The grub shell is different than native grub, running in its own system.

Great news, you were 100% correct.  I used the supergrub cd grub command line and it worked great.  Note to others experiencing this issue, if you're in this command line and it says something about the filesystem after "root (hd#,#)" don't stop just continue with setup (hd#).


SOLVED

---

