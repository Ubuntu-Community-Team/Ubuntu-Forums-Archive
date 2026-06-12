---
title: "Ubuntu 7.1 Install"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by williampr on 2008-03-19
This is a first install of Ubuntu or any Linux distrobution. I am starting fresh clean drives, a Maxtor 100GB UATA boot drive and twin WD 160 GB SATA drives. A CD-RW and DVD RW optical, AMD Athlon 64 at 4,000+ and an MSI 7125 K8N NEO 4-F SLI board. Nvidia chip, 4 SATA connectors, usual IDE HDD and Optical connectors. Lots of air moving and a 500 Watt Antec PS. Nvidia 7600 GT video with 256 of DDR 2 mem and Enspirer bluegears SC with the Oxygen chip. On par price wise with X-Fi will see what it sounds like. I am an X-Fi fan but like to try different things. Stats look impressive for sure. Use on board 1 GB lan and have 3GB of PC 3200 RAM, running dual channel. 

What is the best way to partition the boot or will that be handled by the installation disk? I would like 15 to 25 GB for the OS and other items unique to Ubuntu, and use the balance for programs. The SATA drives can store music and video on one, back up on the other with other starage functions. I can alter any of this according to your advice so if this is not sensible let me know please. I would like a good stable system and more or less room is not a problem. Any tricks or traps I can avoid? I am in virgin territory for me at least, its been all windows previously. I do not OC often and if I do its so slight it just makes me feel like a real daredevil, any effects are not even slightly visible. Sorry this is so long but I tried to hit all my concerns at once. Oh and I am a huge music fan, how does one obtain the best sound from Linux, 5.1 and headphones are my targets, loud but clear sound. Cyberlink Power DVD 7 with upgraded sound is pretty great and X-Fi card and Klipsch Speakers or Logitech Speakers sound pretty good with Windows XP. Thanks so much in advance. My mind is open.

---

### Post by tango_ninja on 2008-03-19
If memory serves ubuntu will allow you partition options during the install. You need only worry about your primary OS drive/partition for now as you can mount your other disks later.

PS have you already  booted Ubuntu from CD ?

---

### Post by Bruce M. on 2008-03-19
> **williampr said:**
> This is a first install of Ubuntu or any Linux distrobution. I am starting fresh clean drives, a Maxtor 100GB UATA boot drive and twin WD 160 GB SATA drives. A CD-RW and DVD RW optical, AMD Athlon 64 at 4,000+ and an MSI 7125 K8N NEO 4-F SLI board. Nvidia chip, 4 SATA connectors, usual IDE HDD and Optical connectors. Lots of air moving and a 500 Watt Antec PS. Nvidia 7600 GT video with 256 of DDR 2 mem and Enspirer bluegears SC with the Oxygen chip. On par price wise with X-Fi will see what it sounds like. I am an X-Fi fan but like to try different things. Stats look impressive for sure. Use on board 1 GB lan and have 3GB of PC 3200 RAM, running dual channel. 

What is the best way to partition the boot or will that be handled by the installation disk? I would like 15 to 25 GB for the OS and other items unique to Ubuntu, and use the balance for programs. The SATA drives can store music and video on one, back up on the other with other starage functions. I can alter any of this according to your advice so if this is not sensible let me know please. I would like a good stable system and more or less room is not a problem. Any tricks or traps I can avoid? I am in virgin territory for me at least, its been all windows previously. I do not OC often and if I do its so slight it just makes me feel like a real daredevil, any effects are not even slightly visible. Sorry this is so long but I tried to hit all my concerns at once. Oh and I am a huge music fan, how does one obtain the best sound from Linux, 5.1 and headphones are my targets, loud but clear sound. Cyberlink Power DVD 7 with upgraded sound is pretty great and X-Fi card and Klipsch Speakers or Logitech Speakers sound pretty good with Windows XP. Thanks so much in advance. My mind is open.

Hi williampr

Welcome to Ubuntu

OK ... forget your "windows mindset" for a moment.

The system ( or root [ / ] ) only needs about 5 Gig max
Your home folder ( /home ) is where programs and config files  go when you install them, so that needs some space.  I recommend that that goes on a separate partition.

Check this out: [psychocats.net]("http://www.psychocats.net/ubuntu/index.php"), specifically these pages:

1. [Plan Partitions]("http://www.psychocats.net/ubuntu/partitioning")
2. Live CD Install: [Installing a Dual-Boot with Windows and Ubuntu]("http://www.psychocats.net/ubuntu/installing#partitioning") Just forget the Window stuff if not needed.
3. Alt CD Install: (I recommend this) [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

Now I don't have what you have but here's what my partitions look like:

Boot Drive: 80 G
/dev/sda1 - formatted: ntfs - mount point: /media/sda1 = Win 2000 - 10 G
/dev/sda2 - extended partition 64.52 G
 /dev/sda5 - formatted rxt3 - mountpoint: **[SIZE="4"]/[/SIZE]** - 20G = root or Ubuntu system ( used 2.68 G )
 /dev/sda7 - formatted ext3 - mountpoint: **[SIZE="4"]/home[/SIZE]** - 40G - programs and stuff
 /dev/sda6 linux swap - 1G

Second HD: 40 G
 /dev/sdb1 - formatted ext3 - mountpoint: /media/sdb1 - all the personal file I want to keep... images, docs backups etc.

---

