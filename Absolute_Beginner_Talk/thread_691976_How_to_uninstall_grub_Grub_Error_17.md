---
title: "How to uninstall grub? Grub Error 17"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by seamonster on 2008-02-09
Hello, Ive decided to uninstall my Ubuntu 6 version.
I got two harddrives. A C: and one H:
The C: got windows installed and some VERY important files. (NTFS)
The H: got 4 partitions. One 2gb (NTFS), one 7gb with ubuntu installed (EXT3), one Extended (500mb) and one Linux Swap (500mb)

Soo.. I got the PartitionMagic on the Windows.. But does it work? Nope!
Since i cant start my Ubutnu (cuz it dosent support my gfx :S) I started my Ubuntu 7.10 Livecd.
I started Gparted and formatted H: to:
One 9gb NTFS and left the two Extended and Linux Swap. 
However, when I now rebooted my computer i got this error:
Grub Loading Stage 1.5
Error 17

And thats all... I cant start windows...
Ive checked the BIOS and Setup but theres nothing that helps...

So basiclly I just need to uninstall Grub right?
But how do I do this from a Ubuntu CD?
Since the Windows (C:) drive is Master and the Ubuntu Drive, now a empty NTFS drive is Slave, i think i have installed the GRUB on windows... or in the BIOS? I dont relly know... i didnt install it :S

Can anyone help?
Thanks!
/Seamonster
And, YES! i have read the other topics but didnt really get it...

---

### Post by overdrank on 2008-02-09
> **seamonster said:**
> Hello, Ive decided to uninstall my Ubuntu 6 version.
I got two harddrives. A C: and one H:
The C: got windows installed and some VERY important files. (NTFS)
The H: got 4 partitions. One 2gb (NTFS), one 7gb with ubuntu installed (EXT3), one Extended (500mb) and one Linux Swap (500mb)

Soo.. I got the PartitionMagic on the Windows.. But does it work? Nope!
Since i cant start my Ubutnu (cuz it dosent support my gfx :S) I started my Ubuntu 7.10 Livecd.
I started Gparted and formatted H: to:
One 9gb NTFS and left the two Extended and Linux Swap. 
However, when I now rebooted my computer i got this error:
Grub Loading Stage 1.5
Error 17

And thats all... I cant start windows...
Ive checked the BIOS and Setup but theres nothing that helps...

So basiclly I just need to uninstall Grub right?
But how do I do this from a Ubuntu CD?
Since the Windows (C:) drive is Master and the Ubuntu Drive, now a empty NTFS drive is Slave, i think i have installed the GRUB on windows... or in the BIOS? I dont relly know... i didnt install it :S

Can anyone help?
Thanks!
/Seamonster
And, YES! i have read the other topics but didnt really get it...

HI and this link is a good info for uninstalling Ubuntu
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by seamonster on 2008-02-09
Now, Ive heard that you can use the Windows CD and go to the consol and type FIXMBR, but... if I dont got any Windows CD?

---

### Post by seamonster on 2008-02-09
> **overdrank said:**
> HI and this link is a good info for uninstalling Ubuntu
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Yeah... But thats the problem :(
I forgot to fix the MBR before uninstalling Ubuntu...
And now I dont know how to recover it...

---

### Post by overdrank on 2008-02-09
> **seamonster said:**
> Yeah... But thats the problem :(
I forgot to fix the MBR before uninstalling Ubuntu...
And now I dont know how to recover it...

 Hi and this may work from that link
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method)

---

