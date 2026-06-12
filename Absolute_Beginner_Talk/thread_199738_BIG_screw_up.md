---
title: "BIG screw up"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-06-19
I think i screwed up big time. I had a ubunutu/xp dual boot. and in an attempt to remove ubuntu from the boot i used the partioner in the install disk to wipe the ubuntu partioner and then i rebooted the system. 

It now fails to load the grub screen showing 

"Error 22"

I tried to reinstall but it just shows a blank blue screen when it should have the partition config screen.


I've got some important files in the windows scetion...HELP!!!

---

### Post by NESFreak on 2006-06-19
grub was installed on the partition you just deleted.
you should restore the windows boot manager.
i think you should run the console thats on the windows install disk and try to run (i think it was, else try finding out the command using help) 'fixmbr'

---

### Post by irv on 2006-06-19
Something like this happen to me awhile back, and as I remember I had to boot with the windows CD and run a utility to repaire the boot sector on the hard drive. But it has been so long ago I am not sure what and how I did it. Oh ya, it was something with MBR

---

### Post by linbetwin on 2006-06-19
Boot your computer with the Windows CD, and wait for the first screen. You'll see an option to press R to repair the system. Press R, then "1" (the number of the Windows installation), then type your admin password for the Windows installation, if you have one (not the Ubuntu password). Then type "fixmbr", ENTER, "y" and again ENTER.

---

### Post by b_martinez on 2006-06-19
Yes, you will need to boot the Windows cd, Chooe the repair option and type in 
fixboot
fixmbr
exit
and it will restore your Windows booting, and re-start the system for you.
Bill

---

