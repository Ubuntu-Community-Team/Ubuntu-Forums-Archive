---
title: "Trying to boot SSD on Mac &quot;Graphite&quot; G4"
date: 2013-02-12
forum: Apple Hardware Users
---

### Post by Javelin Dan on 2013-02-12
[SIZE=2]Running Ubuntu 12.04 Ppc on Mac G4 "Graphics 9Sawtooth)[SIZE=2], 450 Mhz[SIZE=2] processor, 40 G[SIZE=2]B hard drive, 1.5 GB RAM[/SIZE][/SIZE][/SIZE]


I've installed Ubuntu 10.10 Ppc on a Legacy 64 GB SSD (so  I could format it for powerpc and easily determine which drive is booted) via a SATA - USB  adapter. I was able to boot this distro through the adapter, so I know  it's bootable and working correctly. The SSD is now plugged into the  second (gray) hard drive socket on the ribb[SIZE=2]on cable[/SIZE] using  an IDE - SATA adapter. Running the command "lshw" I see the drive  properly formatted and partitioned, but by default the computer always  boots the native hard drive running Ubuntu 12.04. Is there a bootloader  for yaboot (like GRUB in Linux) that allows you to choose at start-up  which drive boots? If so, how would I install it? Or is there some command I could enter at the boot prompt to make this hap[SIZE=2]pen?[/SIZE]
[/SIZE]

---

