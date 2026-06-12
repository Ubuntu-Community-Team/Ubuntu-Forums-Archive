---
title: "unable to boot macbookpro5-3 ubuntu 9.04"
date: 2009-10-06
forum: Apple Hardware Users
---

### Post by skycode on 2009-10-06
Hello,

this is the first time I'm installing ubuntu on a macbookpro but it seems  that I'm unable to boot after install

I'm installing ubuntu 9.04 (64bits) on a macbookpro 5-3. Efi is up to date

I have succeded in repartitioning, installing rEFIt and installing ubuntu from the live cd.  I have install grub in /dev/sda3 (my ubuntu partition)

Then rebooted (btw the laptop doesn't reboot, I have to reboot it by hand but it seems to be normal)

Then in rEFIt resynchronised partition (it actually said they were already sync and did nothing.  I shutdown the machine and boot it under os x fine

When I try to boot it under ubuntu, after selection linux in REFIt, I see a tux for a fraction of second then my screen flashes white a couple of times then nothing happens.  I have to switch it off manually then back on.

does anybody has any idea of how I can debug this ?

Thanks for your help

---

### Post by buntybuntu on 2009-10-07
Hi Skycode,
 
Have you tried running the live cd and see if that boots up properly? Also if that boots up properly, may be you can head over to your /etc/X11/xorg.conf and see the contents of that file. I am no expert, but this is what I did, when I had a minor problem with my graphics. Another option might be to boot into the console mode and then do a "sudo startx" and looking for the error messages if any that appear.
 
Like I said, I am no expert, but this seems like a nice way to start debugging the problem.
 
HTH
 
buntybuntu

---

### Post by amd-64 on 2009-10-07
Two things to try

1. Try booting to recovery mode, if you get to a console, run sudo gdm start and report back any errors
2. In a normal boot, after getting to the blank screen press fn+ctrl+alt+f7 or ctrl+alt+f7 and repeat with f2

Good luck

---

### Post by skycode on 2009-10-14
Thanks all for your help,

Problem is that I never get to see the bootloader, the scrren just goes black when I choose linux in refit ....  So no chance to be able to select recovery boot mode.  However booting from the cd works fine (I actully installed ubuntu that way) .

thanks

---

