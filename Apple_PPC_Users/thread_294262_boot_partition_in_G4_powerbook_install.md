---
title: "boot partition in G4 powerbook install"
date: 2006-11-06
forum: Apple PPC Users
---

### Post by beanworks on 2006-11-06
Hi,

I have a G4 powerbook that has OS X on it and Yellow Dog Linux on it.  I want to replace YDL with Ubuntu 6.06.  The current partition table looks like this:

[FONT="Fixedsys"]/dev/hda1  unknown     .03MB
/dev/hda2  hfs+       4.37GB     
/dev/hda3  hfs        1.00MB             boot
/dev/hda4  ext3       4.16GB    
/dev/hda5  linux-swap  760MB             swap
/dev/hda6  ext3        100MB   

[/FONT]
When I got to the "Prepare mount points" screen, I set the options to:

[FONT="Fixedsys"]/usr       100 MB  Partition 6 (logical) [hda6] (reformat)
swap       761MB  Partition 5 (logical) [hda5] (reformat) 
/            4GB  Partition 4 (primary) [hda4] (reformat)  
/boot     1024KB  Partition 3 (primary) [hda3][/FONT]

(and click Forward)
The Ready to Install screen lists 4, 5 and 6 to be formatted.  But when it begins the install, it goes through partition 4 and partition 6, then stops and gives the message:

No file system is specified for partition #3 of IDE1 master (hda)

and gives the option to go back or continue.

What to do?  I don't really want to reformat that partition if I don't have to (afraid I'll lose access to OS X and have to do a reinstall of that all over again. :(  ).  If I continue, will it mess up the Ubuntu install so I have to go back and do it all over again?:-| 

Thanks for any help!

Carol Bean[FONT="Fixedsys"][/FONT]

---

