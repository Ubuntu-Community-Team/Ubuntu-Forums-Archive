---
title: "12 hours later....hda timeout"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by darqueness on 2008-04-03
So, I just built a new computer, I had it up and running sitting outside on my desk, without a case (live cd ran fine).

Then, i transplant it into a case and bam:

hda: timeout waiting for DMA
hda: drive not ready for command

:confused:

it was running fine a few hours ago, and now it doesnt...

i'v tried running the live cd without a hard disk drive (that should work, right?) and it still didnt work

I'v unplugged/replugged the cables at least a dozen times, reset the mobo, etc...

no idea why it suddenly wont run... please help

---

### Post by darqueness on 2008-04-03
I really just want to know what "hda timeout" means...

---

### Post by joshrobinson on 2008-04-03
did you change any bios settings? or any changes to the hard-drive wires?
is your cdrom/dvdrom on a different ide ribbon then the hard-drive?
are your master and slave correct?

id go in your bios, and check to see if the hard-drives are read fine in there, and that the sizes are correct

---

### Post by Moop on 2008-04-03
If it doesn't work with the hdd disconnected then it could be a problem with your cd drive. Check the connections or try a different one if you have one. 

If it all started when you put the motherboard in a case it could be shorting out somewhere. Also sometimes over tightening the screws can cause problems. My son had a dvd drive that didn't work because he put the screws in so tight it was squeezed between the brackets that held it. 
:guitar:

---

### Post by darqueness on 2008-04-03
K, after a dozen tries, it decided to work... go figure...:confused:

anyway, i'll loosen up the screws a little, buut, there is one more problem

i keep getting a 'failure to create partition' error (i got this before putting it into the case) and cant install xubuntu on the HDD (drive has old xp install that i want to erase)

---

### Post by joshrobinson on 2008-04-03
> **darqueness said:**
> K, after a dozen tries, it decided to work... go figure...:confused:

anyway, i'll loosen up the screws a little, buut, there is one more problem

i keep getting a 'failure to create partition' error (i got this before putting it into the case) and cant install xubuntu on the HDD (drive has old xp install that i want to erase)

its done that to me before, are you installing with a live cd?
i had a partition that i wanted to keep, but had to remove them all due to this error

are you doing manual partitioning? or are you doing the automatic "use entire disc option"
if your doing the entire disc option, go into manual, and delete all of the partitions, then create your new ones

---

