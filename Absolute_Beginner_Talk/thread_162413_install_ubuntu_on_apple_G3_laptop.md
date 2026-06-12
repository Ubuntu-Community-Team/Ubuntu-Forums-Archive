---
title: "install ubuntu on apple G3 laptop"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by ald9n on 2006-04-18
hi i have a strange problem. i want to install ubuntu on a G3 500mhz ibook (384mb ram) only problem is the cd rom is not working (a new cd rom would be the easiest way to go but im still trying to get one shipped to me in oz, in the meantime i want to try something else). 

I was wondering if i could possibly install ubuntu off a 20GB usb drive and if so, how would i do it (tried googling it but nothing).  or if there was another way of installing it (off a networked cd-rom, thru a virtual cd rom like daemon??). if it is not possible let me know.

thanks

---

### Post by dickohead on 2006-04-19
As for the being in Oz thing - I feel your pain! Maybe you could borrow a usb CD-Drive/DVD-Drive? Or get hold of a floppy drive and look into installing via a network... not sure how, but I know it can be done.

And with the 20GB USB drive, can you boot from it? If so, copy the ENTIRE contents of the CD-Rom to the drive, plug it in, set BIOS to boot from it, and away you go... we hope.

---

### Post by markuspm on 2006-04-28
You might need to become familiar with the Open Firmware prompt.
Hold down 4 keys while powering on 'alt' 'Aplple key' 'O' 'F'.
Try 'printenv' to show the config.
Be very carefull what settings you change.
(example: setenv boot-command boot)
To exit enter 'shut-down '.
Netbooting an ibook should be possible.
I googled and found somebody who entered 'boot enet:,ofwboot.xcf enet:/netbsd' at the Open Firmware prompt
to netboot netbsd on an ibook.
Good luck.

PS:
One thing you might find usefull is powering on the ibook while holding the 'alt' key.
It'll bring you to an openfirmware GUI boot selector.

---

