---
title: "[SOLVED] Full Hard drive"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-08-18
Hi there,

I'm swearing like a pirate! Tried installing CNC3  in wine, which I'll have to post about later, which then went and flooded / . Now GDM doesn't load! I have rebooted into recovery mode, deleted all my cached deb's, but still nothing! 

Please help me by telling me how to find large files, where temp files would be stored or where wine would put these accursed files!

and as a bonus why the heck when I cleaned out 1gb+ out of my apt-cache does root still stay 100% full? Any text commands for checking hard drive and folder information would be awesome as well!

Thanks a lot!


Rudolf

---

### Post by nitro_n2o on 2007-08-18
use "du" like this 
```
sudo du -a /  | sort -nr 
```
in many cases the /var partition is filled quickly so 
```
sudo du -a /var  | sort -nr | head 
``` to see the top 10 largest
you can also 
```
sudo du -a --si /var | sort -nr | head
``` for a human readable format

---

### Post by RudolfMDLT on 2007-08-18
Hi,

Thanks for the help - though I'm gonna  need a little more! :)
Using this command:
> root@rh:~# sudo du -ah / | sort -nr | head --lines=30
1020K   /usr/share/gnome/help/synaptic
1020K   /usr/share/apps/kig/icons/hicolor
1020K   /usr/lib/libdb-4.4.so
1020K   /stuff/pics/Vusi/P3080109.JPG
1020K   /stuff/pics/Vusi/P3080107.JPG
1020K   /stuff/pics/Vusi/P3040106.JPG
1020K   /stuff/pics/Personal/Ski 2005.02.26/P1010087.JPG
1020K   /stuff/pics/Personal/ski 2004.10.24/P2210034.JPG
1020K   /stuff/pics/Kgalagadie/P4270187.JPG
1020K   /stuff/pics/Helpmekaar/Rugby/Germiston20050507/P5070001.JPG
1020K   /media/disk/WINDOWS/system32/drivers/hsfdpsp2.sys
1020K   /media/disk/WINDOWS/system32/CatRoot/{F750E6C3-38EE-11D1-85E5-00C04FC295EE}/sp2.cat
1020K   /media/disk/WINDOWS/ServicePackFiles/i386/hsfdpsp2.sys
1020K   /media/disk/WINDOWS/$NtServicePackUninstall$/cimwin32.mof
1020K   /media/disk/Program Files/Lionhead Studios/Black & White 2/Data/ctr/a_siren_appear.lhca
1020K   /media/disk/Program Files/Lionhead Studios/Black & White 2/Audio/Music/TownAlignment/norseg3.ogg
1020K   /home/rudolf/.mozilla/sunbird/1v0evhgs.default/XPC.mfasl
1020K   /home/rudolf/matlabinstall/toolbox/images/imdemos/tissue.png
1020K   /home/rudolf/matlabinstall/toolbox/dspblks/dspblks/@dspfixptddg
1016K   /usr/src/linux-headers-2.6.20-15/include/asm-sparc64
1016K   /usr/share/locale/tr/LC_MESSAGES
1016K   /usr/share/groff
1016K   /usr/share/consolefonts
1016K   /usr/lib/libpthread.a
1016K   /stuff/pics/Zanzibar 2004.12.12/P4130066.JPG
1016K   /stuff/pics/Zanzibar 2004.12.12/P4110019.JPG
1016K   /stuff/pics/Personal/ski20070218/P1090012.JPG
1016K   /stuff/pics/Personal/Ski 2005.02.26/P1010083.JPG
1016K   /stuff/pics/Personal/matriekafskeid/stephane s`n 060.jpg
1016K   /stuff/pics/Personal/JAG/P1010100.JPG


Now, removing the -h for human readable from:

> root@rh:~# sudo du -a / | sort -nr | head --lines=30
156797633       /
85397164        /stuff
46749949        /media
25395925        /media/disk
21354012        /media/New Volume
17383076        /stuff/ISOsandMovies
16430860        /stuff/Music
13645024        /virtualmachines
13644992        /virtualmachines/Windows XP Professional
10465000        /stuff/pics
10459881        /media/disk/Program Files
10330312        /stuff/Music/Pre2005
7105704 /stuff/Jackass_the_movie.iso
6799152 /stuff/pics/Personal
6047514 /media/disk/Unreal Anthology
6001162 /media/disk/Unreal Anthology/UT2004
5866672 /media/disk/Program Files/Electronic Arts/Command & Conquer 3
5866672 /media/disk/Program Files/Electronic Arts
5607956 /stuff/Eragon
5429216 /stuff/CNC.iso
5428720 /stuff/cnc
5423244 /media/New Volume/cnc
4274128 /stuff/rip
4273968 /stuff/rip/db
4273964 /stuff/rip/db/lk2
4237520 /stuff/rip/db/lk2/vob
4237516 /stuff/rip/db/lk2/vob/001
4198420 /stuff/rip/db/lk2/vob/001/VIDEO_TS
4181352 /stuff/ISOsandMovies/Iceage2
4167976 /stuff/ubuntu 7.04 i386.iso


Isn't this a little weird?


Anyway /stuff is a folder mounted on a different drive and when I only search in the /var folder, the largest files that it finds are small .xml files?

Maybe something wrong with the file system - though I seriously doubt it? whats the linux command for Check disk? 

any other ideas?

Thank you very much for your help thus far!

---

### Post by RudolfMDLT on 2007-08-18
bump...

I Know I should be bumping a thread this early but I really need to get this resolved! I can't boot my system! Please - anybody with any idea, please help!

Thanks!

---

### Post by schorsch on 2007-08-18
> **RudolfMDLT said:**
> Hi,
Now, removing the -h for human readable from:
Isn't this a little weird?

No, it is not weird .....as noone told you to use the parameter "h" when  using the command "du". If you do this the piped command "sort -nr" will assume, that 10G are smaller as 11 MB, as it only uses the numeric value when sorting.. ;-)
You should use the following command to stay on the filesystem that / lives on:

```
sudo du -ax / | sort -nr|head -30
```

... and also the output of "df -h" would be helpful.

Have you deleted the files via nautilus? Then they will end up in the .Trash directory in your home directory and will use the same space as before ....

---

### Post by RudolfMDLT on 2007-08-18
Thanks schorsch, I have solved the big file issue now. Wine ran as root and so installed into root's home folder and filled up the drive. 

GDM still won't load so I'll start a new thread on that! Thanks for the help!

---

