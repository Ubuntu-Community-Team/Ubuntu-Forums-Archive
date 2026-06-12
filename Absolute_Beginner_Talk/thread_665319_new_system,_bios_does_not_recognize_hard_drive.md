---
title: "new system, bios does not recognize hard drive"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by juanzo007 on 2008-01-12
hey folks,...

new system i've put together.  had a problem previously with the monitor not displaying and found out i didn't connect the 4 prong 12v connector.  now the monitor works and i can get into bios, but it isn't recognizing the sata HDD.  before i fixed the original problem, the HDD was spinning away!

Any suggestions?

---

### Post by mikeyphi on 2008-01-12
> **juanzo007 said:**
> hey folks,...

new system i've put together.  had a problem previously with the monitor not displaying and found out i didn't connect the 4 prong 12v connector.  now the monitor works and i can get into bios, but it isn't recognizing the sata HDD.  before i fixed the original problem, the HDD was spinning away!

Any suggestions?

The most probable cause (which no doubt you've checked) is a poor connection.
Tripple-check both data and power connections!!!!

---

### Post by juanzo007 on 2008-01-12
double, triple checked, multiple connections, sata ports...  was recognized before and now is not?  i tried to install ubuntu once but when it tried to install partitions, i got "no root system is defined" as was unable to install conmpletely...

---

### Post by juanzo007 on 2008-01-12
i do remember for some reason it had shown my hdd initially as being a second master, not primary.  not sure why, i plugged into the #1 sata port...

---

### Post by skymera on 2008-01-12
make sure the drive is enanled in the bios.

when i got a new drive i had to enable it in the bios

---

### Post by juanzo007 on 2008-01-12
if u mean enabling sata under ide config, yes, it is...  btw i also cleared cmos as well, if that matters

---

### Post by juanzo007 on 2008-01-12
bump

---

### Post by logos34 on 2008-01-12
> **juanzo007 said:**
> if u mean enabling sata under ide config, yes, it is...  btw i also cleared cmos as well, if that matters

in the hard disk section is it set for 'auto', LBA?

give us the make and model of the hdd and mobo

---

### Post by juanzo007 on 2008-01-12
thanks!!  

Asus p5gc-mx/1333 motherboard
seagate sata 300 500GB HDD

Hard disk section within bios is auto.

---

### Post by juanzo007 on 2008-01-12
btw, when i first succesfully entered bios, my hdd wasn't listed as primary master, i think it was 3rd??  can't remember.  

but it was listed, and when i went for the ubuntu install, i could only get as far as partitioning error "no root system is defined"...

---

### Post by logos34 on 2008-01-12
> **juanzo007 said:**
> btw, when i first succesfully entered bios, my hdd wasn't listed as primary master, i think it was 3rd??  can't remember.  

but it was listed, and when i went for the ubuntu install, i could only get as far as partitioning error "no root system is defined"...

'primary master' is ide-talk...Sata disks are all 'master' because each is on its own dedicated chennel.  Maybe it was plugged into the 3rd channel. (or last if it's like mine and starts numbering at 'SATA 0').

---

### Post by logos34 on 2008-01-12
> **juanzo007 said:**
> when i went for the ubuntu install, i could only get as far as partitioning error "no root system is defined"...

did you choose 'manual' partitioning option?

Does Gparted on the live cd desktop see the disk? (system>admin>gnome part editor)

---

### Post by juanzo007 on 2008-01-12
i can't get to a manual partition option.  I get to partition setup, then the "no root stsem defined" error.

gnome partition editor is installed in applications, but i can't find it anywhere among the drop down menus at the top of the desktop.

---

### Post by logos34 on 2008-01-12
it was under system>admin last time I looked

try this:

open a terminal and type
[B]
sudo fdisk -l[/B]

anything?

---

### Post by juanzo007 on 2008-01-12
i tried sudo fdisk -s partition, says it could not find partition
no response from fdisk -l

---

### Post by logos34 on 2008-01-12
not sure what to tell you...you've checked connections, bios settings and still ubuntu doesn't see it.  Nor fdisk.  Maybe try plugging it into each of the remaining sata ports.  I'm fresh out of ideas.  It's sata so this isn't a cable or jumper issue.  Maybe the drive is DOA.  (not uncommon with shipped bare drives--they get banged around.  But then maybe you bought a boxed retail kit.  dunno).

---

### Post by juanzo007 on 2008-01-12
Thanks for all the help, bro...  Per normal, operator error - I managed to fry the hard drive -  oops!  Fry's was cool and let me exchange it.  Thanks again...

---

