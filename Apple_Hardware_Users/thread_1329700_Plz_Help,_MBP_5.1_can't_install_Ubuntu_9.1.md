---
title: "Plz Help, MBP 5.1 can't install Ubuntu 9.1"
date: 2009-11-17
forum: Apple Hardware Users
---

### Post by maximilianyuen on 2009-11-17
New problem at post #4



----------------------------
Well, first of all please let me say that I have google, search here, and read this [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)


my problem: can;t get the live CD loaded. ISO not corrupted as I have successfully installed it in VMware, and the disks I burned are fine(I tried 3 disks), and I burn in min speed


my steps:

I create 30G of space on HD using Bootcamp Assistant, done then restart myself
in rEFIt no CD is showing, and I read that it don't support media, so I restart, press Option.

then, other than the HD/rEFIt part, there is a bootup part with a CD image named "WINDOWS"
I assume this is the Live CD so select it, then black screen, and it said

"no bootable device, press anykey to reboot"

and my keyboard doesn't respond, which is normal somehow, so I hold the power button

then, I run the rEFIt inspector (not sure the name, but the only utility there) that in the rEFIt boot menu, and it give a list of HD thing which I don't understand, and ask me yes or no, and I select yes, seeing no harm trying.

and then there is a Tux image appear in rEFIt, other than the bootcamp/windows and mac HD
I happily click into it and but again,

"no bootable device, press anykey to reboot"

--------------

well I am no expert in computer thing but I am pretty sure I follow the step of the install guide fully, except that I have installed rEFIt the first of all. 

Please let me know if I miss out any info for all pros here to kindly help solving my problem....

Thanks in advance

---

### Post by maximilianyuen on 2009-11-17
PS: I really think it is the problem of the disk, but I do a MD5 compare between the disk and the image and its the same......

so please advice....I am really exhausted :(

---

### Post by zAfi on 2009-11-17
did you "burn the iso on the disc" or did you "burn the iso"? What I'm trying to say, when you mount the burnt disc, do you see the iso file or do you see contents (files, folders)? Just in case as this happend to me the last time and I'm quite experienced... :P FYI, you need the content on the disc... ;)

---

### Post by maximilianyuen on 2009-11-17
> **zAfi said:**
> did you "burn the iso on the disc" or did you "burn the iso"? What I'm trying to say, when you mount the burnt disc, do you see the iso file or do you see contents (files, folders)? Just in case as this happend to me the last time and I'm quite experienced... :P FYI, you need the content on the disc... ;)

well, thanks but lucky enough I didn't fall for that this time (I did last time)

it turns out my MBP didn;t read the disk my iMac burn correctly -.-

anyway now I have installed and right to the last step...and problem again T_T

the pic said it all....
please help...

I suspect that is the windows bootcamp loader thing as I did not delete the bootcamp partition in ubuntu setup, but I did it in Mac Disk Utility......
[IMG]http://farm3.static.flickr.com/2552/4112774383_4eae195a5e_b.jpg[/IMG]

---

### Post by maximilianyuen on 2009-11-17
PS: now it didn't allow me to fix the boot table thing and so I can;t boot into my ubuntu.....


I guess i just need to delete that "unknow" sector then it's alright? (I surely hope)

if yes, can anyone please advice how can I do so?

Thanks again....

---

### Post by Nohtanhoj on 2009-11-17
Your problem is not because you deleted the partition in Disk Utility... I deleted it in GpartEd and I have the same issue currently. Don't delete that Unknown partition. It might serve some EFI purpose, and deleting it might make your entire computer un-bootable.

This thread should help you out. [http://ubuntuforums.org/showthread.php?t=1297229&highlight=GPT+partition+type+unknown+found](http://ubuntuforums.org/showthread.php?t=1297229&highlight=GPT+partition+type+unknown+found)

Currently, I'm actually having the same problem with my iMac 24", and I plan on giving the stuff in that thread a try when I get some time away from school...

Good luck!

---

