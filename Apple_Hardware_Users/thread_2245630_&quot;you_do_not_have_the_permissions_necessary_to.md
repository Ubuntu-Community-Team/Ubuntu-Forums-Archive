---
title: "&quot;you do not have the permissions necessary to view the contents of...&quot;"
date: 2014-09-25
forum: Apple Hardware Users
---

### Post by Fritz_Pape on 2014-09-25
Hey, so here's my dealio:

My MacBook hard drive stopped booting up. I got a SATA to USB cable but the hard drive wouldn't show up on my PC nor my Mac (which I had a spare hard drive for), so somebody suggested I try ubuntu. I installed it on a USB drive and booted my computer up from it, and lo and behold the hard drive showed up. 

But, I can't access my files and etc from the user folder. Any time I open anything inside the user folder that message pops up. I did a bit of searching and I found stuff about [COLOR=#000000]sudo or gksudo, but I don't know how to bring those up from a USB boot. 

Anyone able to help me out??[/COLOR]

---

### Post by coldcritter64 on 2014-09-25
1. With the machine booted into Ubuntu go into the /media folder and note the folder you wish to access. 
2. Open a terminal and type in "gksudo nautilus " (without the quotes and *_note the extra space after the word nautilus, include it as well_*). 
3. Drag and drop the folder for the drive in /media into the terminal, this will complete the gksudo command to open the drive mount point in the file manager "nautilus".
4. Press the enter/return key on the keyboard and the old hard drive should now open in Nautilus as root user. **BE CAREFUL when using a file manager as the root user, you can do serious damage to an installation** if an error occurs while operating as root, data can be very easily destroyed accidently.

Provided the drive is physically ok, this should allow you to access/copy any files off the old drive by bypassing ownership and permissions while logged into nautilus as root with "gksudo".

Remember to close the root nautilus window as soon as you recover your data, use the root browser window for the absolute minimum you require to avoid potential accidents. You may need to adjust file/folder ownership and permissions back to a normal user account after using this for the recovered files/folders, check out the man pages for usage of the "chown" and "chmod" commands to do so eg, (in a terminal) "man chown" or "man chmod" (once again, without the quotes).

Good luck :)  Edit: OP, please note Vladlenin5000's next post re "hfs+ tools", that may be needed to be installed to fully access the contents.

---

### Post by Vladlenin5000 on 2014-09-25
Hi, welcome.

First of all, *sudo* and *gksudo* are command to elevate the privileges to the system, for installing/removing software or any other modification at the system. It isn't for accessing password protected contents.
You have several issues here:
1) The HDD was in a MacBook therefore it already has a proprietary file system not quite well supported anywhere outside the Apple ecosystem. At best you'll be able to mount it read-only in Ubuntu. You need to install HFS+ tools from software center (just search "hfs+")
2) The HDD stopped booting... Why? Are you sure it's software (OS) problem only? If not then it's probably faulty so why bother?

---

### Post by slickymaster on 2014-09-25
*Moved to the ***Apple Hardware Users*** sub-forum*

---

