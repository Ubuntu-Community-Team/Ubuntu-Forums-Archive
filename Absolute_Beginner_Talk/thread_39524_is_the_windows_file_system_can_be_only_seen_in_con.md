---
title: "is the windows file system can be only seen in console"
date: 2005-06-05
forum: Absolute Beginner Talk
---

### Post by bonusiso on 2005-06-05
i mounted my windows file system :

# monut /dev/sda1 /mnt/winc

but i can see it only in terminal -console-(which one you use)  and i have some documents which i need and i dont wanna coppy it to the linux file system. :grin:

---

### Post by snds24 on 2005-06-05
[QUOTE=bonusiso]i mounted my windows file system :

# monut /dev/sda1 /mnt/winc

but i can see it only in terminal -console-(which one you use)  and i have some documents which i need and i dont wanna coppy it to the linux file system. :grin:[/QUOTE]

Mayby you have to use #sudo /mount/ dev/sda1 /mnt/winc ?
And did you create /mnt/winc directory?

---

### Post by bonusiso on 2005-06-05
i did it as a root !!!

i can see it in terminal!

it had been mounted but i couldnt open it because the owner is root and i cant open it without console :)

---

### Post by az on 2005-06-05
I have a window98 partition in french.  My fstab entry looks like this:
/dev/hda1       /win            vfat    iocharset=iso8859-1,umask=000,quiet,codepage=850        0       0


Users can mount it and browse it.

---

### Post by bonusiso on 2005-06-05
ding dong 

new question i cant find my fstab ??? how can i found it or may i have to create it?????

---

### Post by snds24 on 2005-06-05
[QUOTE=bonusiso]ding dong 

new question i cant find my fstab ??? how can i found it or may i have to create it?????[/QUOTE]

my is in /etc/fstab   and i think yours is there as well  :)

---

### Post by bonusiso on 2005-06-05
i found it !!!


it includes that: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


what i sould do next????

---

### Post by betrayed on 2005-06-05
[QUOTE=bonusiso]i found it !!!


it includes that: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


what i sould do next????[/QUOTE]
 [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)  Probably should chec that out.  It should point you in the right direction

---

### Post by bonusiso on 2005-06-05
thanks you betrayed you are my hero !!!!!  :razz:

---

### Post by snds24 on 2005-06-05
in the teminal:
sudo mkdir /mnt/winc 
(if you didn't create this directory before)
sudo cp /etc/fstab /etc/fstab_backup
(just to backup you fstab file.)
sudo gedit /etc/fstab
(opens the fstab file with gedit.)

In gedit add to the text

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
**/dev/sda1  /mnt/winc  vfat    umask=000       0 0**
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Don't forget to save the file. Try once more:
 #sudo /mount/ dev/sda1 /mnt/winc
BTW after reboot no need to execute this command.

---

### Post by snds24 on 2005-06-05
[QUOTE=bonusiso]thanks you betrayed you are my hero !!!!!  :razz:[/QUOTE]
I am late  :)

---

### Post by bonusiso on 2005-06-06
thank you too your advise is also very useful and in fact it is what i need because i fed up with mounting always when i open my computer!!!

---

