---
title: "prob installing edgy"
date: 2006-12-18
forum: Apple PPC Users
---

### Post by darkdragoon on 2006-12-18
HI i am usieng a external harddrive to runmy computer i have two partion with 10.2 and one wit nothing on it. i downloaded the ubuntu_powerpc_dapper the ubuntu-6.06.1-desktop-powerpc.iso. how do i install in on a firewire drive. my internal harddrive is dead and don't work. that's why i am running my computer off my external firewire drive. which is made by western digital 250gb. all respones would reall help. thanks.

okay i've downloaded the edgy version and burned it to a cd.  and when i boot from the cd and hit enter i get the unbuntu thing and that bar that goes back in forth then i get this 

/bin/sh:can't access tty ; job control turned off.

i have idea what this mean i've never used linux before.  
can anyone help sorry for the reposting...

---

### Post by stream303 on 2006-12-18
Ubuntu can be run from an external firewire drive, although I'm not sure how much effect a dead drive is having on your system.

The main problem is that even though you may be able to install it on the external firewire drive, it is a pita to "bless" it, or make it bootable.  The installer will complain that it can't finish the ybin process, so you have two options at that point:

1) drop to a shell and use parted to bless it manually, or 
2) use an already-booted version from the internal drive to bless the external drive.

The other issue is that you will have to manually figure out your openfirmware root/boot paths and edit your yaboot.conf file manually before issuing the ybin -v command.

This problem is not specific to Ubuntu - I'm running Debian Etch on my firewire and had to do the manual steps.

Search the PPC forum for "firewire" and see if this is something you want to tackle up front.  It might be easier just to replace your internal drive if you are starting out.

I have some notes here on how I did it from an already-working install of Ubuntu Edgy on my internal drive:
[http://www.ubuntuforums.com/showthread.php?t=314237](http://www.ubuntuforums.com/showthread.php?t=314237)

---

### Post by darkdragoon on 2006-12-18
well i have a partion with 10.2 and and empty partion i am able to use the external drive to boot of .  i guess i'll try what you did.

---

