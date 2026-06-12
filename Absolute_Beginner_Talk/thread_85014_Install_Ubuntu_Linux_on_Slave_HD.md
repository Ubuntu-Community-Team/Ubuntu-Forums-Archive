---
title: "Install Ubuntu Linux on Slave HD?"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by jeffreyvergara.NET on 2005-11-01
Hello, I currently planning to reinstall Ubuntu. I have 2 Hard Disk, [COLOR="Red"]hda1[/COLOR](Master) and[COLOR="Blue"] hdb1[/COLOR](Slave). I have my Ubuntu currently installed in [COLOR="Red"]hda1[/COLOR] (80gb,7200rpm), I wan to install a new Ubuntu to my [COLOR="Blue"]hdb1[/COLOR] (40gb, 5200rpm) and reformat my [COLOR="Red"]hda1[/COLOR] and use it as my backup disk.

If I install Ubuntu on my [COLOR="Blue"]hdb1[/COLOR](40gb) HD, will the grub boot loader still detect my old ubuntu installtion on my [COLOR="Red"]hda1[/COLOR](80gb)? or It will just be replaced by the new grub installed in [COLOR="Blue"]hdb1[/COLOR](40gb)?

---

### Post by teaker1s on 2005-11-01
from memory If you install ubuntu on slave it automatically alters mbr on primary harddisk a better solution would be to just have the harddisk you want ubuntu on set to primary master install ubuntu then power down and install other harddisk-otherwise.
1 some motherboards will only boot primary master
2 you will get slow boot as grub asking which harddisk to boot eack time and if you miss the options it will default boot pri master after delay

hope this helps

---

### Post by Kapre on 2005-11-01
[QUOTE=jeffreyvergara.NET]Hello, I currently planning to reinstall Ubuntu. I have 2 Hard Disk, [COLOR="Red"]hda1[/COLOR](Master) and[COLOR="Blue"] hdb1[/COLOR](Slave). I have my Ubuntu currently installed in [COLOR="Red"]hda1[/COLOR] (80gb,7200rpm), I wan to install a new Ubuntu to my [COLOR="Blue"]hdb1[/COLOR] (40gb, 5200rpm) and reformat my [COLOR="Red"]hda1[/COLOR] and use it as my backup disk. [/quote]

If you don't have anything to back up on hda1, just erase it and go with the new install on hdb1.

> If I install Ubuntu on my [COLOR="Blue"]hdb1[/COLOR](40gb) HD, will the grub boot loader still detect my old ubuntu installtion on my [COLOR="Red"]hda1[/COLOR](80gb)? or It will just be replaced by the new grub installed in [COLOR="Blue"]hdb1[/COLOR](40gb)?

If you erase it (hda1) before installing the new ubuntu on hdb1, it wouldn't be detected anymore.

K

---

### Post by jeffreyvergara.NET on 2005-11-01
I can set my bios to boot from hdb1(slave) so It will not be a problem right? Another issue Im concern about is what will be the performance if I install Ubuntu on my 5200rpm HD instead of the current 7200rpm(hda1)...

and how do I full format my hda1(80gb)? qtparted in Live CD? and what will be the best filesystem format for my backup disk? Fat32, ext2, ext3, etc...? 

I'll never gonna use Window$ again so im having thoughts on using Fat32 again...

anyways.. Thanks ^_^

---

### Post by Kapre on 2005-11-01
[QUOTE=jeffreyvergara.NET]I can set my bios to boot from hdb1(slave) so It will not be a problem right? Another issue Im concern about is what will be the performance if I install Ubuntu on my 5200rpm HD instead of the current 7200rpm(hda1)...[/quote]

I'm running my Ubuntu on a 5400rpm (maxtor 20 gig - hdb1) and a 7200rpm (seagate 160 gig - hda1[xandros, fc4, xp]) and I'm preety happy with the performance of it.

>  and how do I full format my hda1(80gb)? qtparted in Live CD? and what will be the best filesystem format for my backup disk? Fat32, ext2, ext3, etc...? 
Since you'll dump M$, I would suggest ext3 (there maybe someone else who can give you ideas)

>  I'll never gonna use Window$ again so im having thoughts on using Fat32 again...anyways.. Thanks ^_^

E-X-C-E-L-L-E-N-T (ala Mr. Burns)

K

---

### Post by jeffreyvergara.NET on 2005-11-01
[QUOTE=kapre]If you don't have anything to back up on hda1, just erase it and go with the new install on hdb1.[/QUOTE]
I have almost 40gb of data for backup, but I guess i can just burn them.. lol

my plan is, backup my files on [COLOR="Blue"]hdb1[/COLOR](40gb) to [COLOR="Red"]hda1[/COLOR](80gb) **>>>** reboot, set my bios to boot from [COLOR="Blue"]hdb1[/COLOR],** >>>** format and install Ubuntu in [COLOR="Blue"]hdb1[/COLOR] (or FULL format 1st[COLOR="Blue"] hdb1 [/COLOR]using live cd's qtparted??? then install) **>>>** use the remaining free space of [COLOR="Blue"]hdb1[/COLOR] to transfer files from [COLOR="Red"]hda1 [/COLOR]>>> reformat [COLOR="Red"]hda1[/COLOR] >>> backup file to [COLOR="Red"]hda1[/COLOR].

[QUOTE=jeffreyvergara.NET]I'll never gonna use Window$ again so im having thoughts on using Fat32 again...[/QUOTE]
---off topic----
but it most cases i'll use Window$ outside... lol, our school use Window$ and there's only 1 internet cafe using Ubuntu here in our area, and majority of the Internet cafe's here uses illegal copies of Window$ and other softwares...

---

### Post by jeffreyvergara.NET on 2005-11-05
thanks guys for all of your support, however I still have 1 question left... hehehe..

What I did was I just changed the PIN of the harddrive so my slave becomes Master. I have Installed Ubuntu on both of my Harddrives, HD1 is my default Ubuntu, and I'm planning to delete files & folders on HD2. I cannot format it because of GIG of data I havnt backup yet.

The question is, will it be alright if I just delete folders on the Disk? like, etc,bin,dev,media,etc...?

---

