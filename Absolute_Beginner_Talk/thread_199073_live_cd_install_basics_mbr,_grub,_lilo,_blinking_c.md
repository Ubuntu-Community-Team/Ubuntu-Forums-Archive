---
title: "live cd install basics: mbr, grub, lilo, blinking cursors, umeshu"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by takayuki on 2006-06-18
Hi,

i've got an old test box: compaq presario 2298 (japanese model), that i'm trying to install linux  on.  

the first time i tried the ubuntu dapper live cd, it booted from the cd as it should, but then the installer froze... pain, agony ensued, etc.

after that, i couldn't get anything to boot via cd or otherwise.

so i took the hardrive out, connected it to my osx box, and formatted the hd.

when i put it back in the compaq, it booted the live cd again, but again, the installer froze.

**Why did i have to format the drive for the live cd to work?

**Is it because the MBR was messed up?

But in the compaq BIOS, it's has CD drive as the first thing to try to boot from...

any thoughts greatly appreciated.

-takayuki

---

### Post by u.b.u.n.t.u on 2006-06-18
You don't need to format a HDD to run a live CD.

compaq presario 2298 = CPU? RAM? Video MB? HDD size?

---

### Post by takayuki on 2006-06-18
ubuntu,

thanks for the reply.

here are the specs: &#65347;&#65360;&#65365;400MHz&#65380;64MB&#12289;8GB&#12289;56Kbps&#12289;32x &#65315;&#65316;&#65293;&#65330;&#65327;&#65325; Windows 98

i hear what you are saying about not needing to format the hd for a live cd.  you don't even need a hd in the computer to boot.

but... 

i just used a win95 boot floppy to erase the hd.  when i rebooted, my  gparted live cd suddenly booted.  (i'd left it in from a previous unsuccesful attempt.)

when the win95 floppy booted, it was the first time the computer had booted in a few days of trying to get various linux live cd's going.  

before the hd erase, all i got when trying to boot a live cd was a blinking cursor in the upper left corner of the screen.  i couldn't type in anything.

who knows?  i'm a flailing newbie.  having fun, of course. :)

i'm installing xubuntu now.  any thoughts on what is happening, as always, greatly appreciated.

takayuki

---

### Post by takayuki on 2006-06-25
Hi,

if anyone has a similar situation.  i did find a fix. the old cdrom drive was bad.

i replaced the cdrom drive, and now i can boot most live cd's no problem.

i also found that a few of the cd's i'd burned would not work on the new drive and were bad from the start.

so there it is.  if you get cd and cd drive funkiness, make sure you've got a working cd drive and your cd's are ok too. obvious advice from a moron. i've now started checking the md5sum on all iso images before i burn.

Ok, let's put this one to bed.
Goodnight, Johnboy.  Goodnight, Grandma.

---

