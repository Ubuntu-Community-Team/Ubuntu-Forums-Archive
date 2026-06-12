---
title: "Boot Error After Install"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by harryalder on 2008-04-05
Hi,

I'm new to Linux and to Ubuntu.  I downloaded the 7.1 image, burned it to disk, and ran it on my laptop.  After the CD booted up I clicked on the desktop icon for Install and went through the prompts to install to the hard disk.  After rebooting I received the message to remove the CD and press Enter to reboot.  The system started to reboot and then gave me the message:

GRUB Loading Stage1.5.

GRUB loading, please wait

Error 18

At this point I get a black screen with  the above three lines at the top.

Any help would be greatly appreciated.

Thanks!

Harry

---

### Post by upthelum on 2008-04-05
Have a look [_*here*_]("http://ubuntuforums.org/showthread.php?t=11764").

---

### Post by bumanie on 2008-04-05
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18) is probably the best site about grub.

---

### Post by harryalder on 2008-04-08
Hi,

Thanks for the help.

After reading the above recommended posts I believe that my problem is that I am installing on a 250GB drive in a machine that will see up to 137GB.  One of the recommended solutions was to create a 2GB boot partition on the drive during installation.  Unfortunately it did not mention how to do this.  I am absolutely new to Linux and it's disk layouts and nomenclature.  I have the following when the installer partition manager opens during installation:

/dev/sda
   /dev/sda1    ext3    /media/sda1    4926 mb        2300 mb
   
    free Space                                     243591 mb
  
  /dev/sda5                swap                1538  mb          0 mb


Any suggestions as to what I need to do here.  If there is a writeup about this, please let me know.

Thanks!

---

