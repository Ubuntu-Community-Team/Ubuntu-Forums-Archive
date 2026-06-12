---
title: "Dual Boot Question"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-08-10
Hi,

I have (it seems) succesfully install Ubuntu (very easy) and then Windows XP (terribly difficult) on my IBM R32.  Everything has been partitioned and seperated and appears to work.

Thanks for your help!

How do I, however, make it easy to choose which OS to boot to when I start my computer ?  As of now, it is booting automatically into Windows ... I was running Ubuntu for a while but I can't get it to boot into there again.

I looked in my BIOS but it just has an option of selecting the "HARD DRIVE" ... and if I get to the option (via F12) of selecting my boot device, I can't differentiate between partitions.

Any ides ?  I think ubuntu is still on there (it better be!) but I can't get to it.

Thanks,
Damon

---

### Post by loserboy on 2006-08-10
I think I know whats goin on here 

did you install windows after ubuntu?    if so your windows wrote over grub (the program that lets you choose your OS)

theres a couple ways to fix this, and some howtos on it as well, try searching "grub" or "reinstall grub"

let me know if you can't find anything

Edit: oh yea  most likely ubuntu is still there

---

### Post by Tomosaur on 2006-08-10
You will need to reinstall grub. You should always install linux AFTER windows, since Microsoft doesn't believe any other OS has the right to exist :/

---

### Post by thornomad on 2006-08-10
Thanks -- I didn't have a windows install disk, which is why I put Windows on second ... and, I wasn't sure whether windows would preserve my "secret" partition (given to me by IBM).

I looked around for re-install grub and found: 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub-install%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub-install%29)

I will try those suggestions.

Thanks!!

Damon

---

### Post by loserboy on 2006-08-10
nm u found it

---

### Post by thornomad on 2006-08-10
Do I want to [COLOR="Red"]overwrite[/COLOR] or [COLOR="Red"]preserve[/COLOR] my windows boot loader ?

---

### Post by thornomad on 2006-08-10
Okay, so here is what I tried:

[LIST=1]
[*]Booted to live CD
[*]Ctrl-Alt-F1
[*]typed in "sudo -l"
[*]typed in "grub"
[*]typed in "find /boot/grub/stage1" (which reported hd0,5)
[*]typed in "root (hd0,5)"
[*]typed in "setup (hd0,5)"
[*]typed in quit
[*]typed in reboot
[*]went straight to windows
[/LIST]

Anymore ideas ?

D

---

### Post by loserboy on 2006-08-10
you want to overwrite.

> # typed in "root (hd0,5)"
# typed in "setup (hd0,5)"

try using 

# typed in "root (hd0)"
# typed in "setup (hd0)"

instead.

i think that will put it in the right spot, anyway thats what i did (removing the second number is _supposed_ to put it in 0,0,0 which is where the mbr is)

---

### Post by loserboy on 2006-08-10
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

this place has a bootable grub installer thats suppose to do everything automatically if my last post doesnt help.

also you might just reinstall ubuntu, you aren't gonna run out of registration codes   :D

---

### Post by thornomad on 2006-08-10
I resovled the problem by re-installing ubuntu from the Live CD completely ... in cluding re-partitioning the drives (not the windows volume).

After that, grub ran perfectly.

Thanks!

---

