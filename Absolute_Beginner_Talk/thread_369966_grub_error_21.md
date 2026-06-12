---
title: "grub error 21"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by eldeu on 2007-02-25
hi,

having a problem, i know why, but no idea how to solve it...

the thing is i installed ubuntu in a usb external hard drive, while i have windows xp in my laptop´s hard drive.

so, when i start my computer with the usb hd connected, no problem, grub gives me the option to choose between windows and ubutu, and they both work ok. But if i want to start the computer without the external hd connected, it wont load anythin an the message "error 21" comes out without any os loading.

i understand that the grub program is installed in the external hard drive, but i would like to be able to load windows when the hard drive isn´t connected.

i read from someone having the same problem that a good solution could be downloading "grub4dos", a grub that works with windows... i did download it, using windows, but i have no idea how to install it or use it.

thank you so much in advance, greetings from spain

---

### Post by Gerry Atric on 2007-02-25
Don't know if this will help as I am not well versed in setting up Ubuntu, but I recently had a problem with Grub error 21 and found that it was because my bios settings were not finding the drive. I went into the bios/cmos startup and fiddled until all drives were found. You could have a problem with the grub being installed on the external "S" drive as well, might be better in the main hard disk mbr with Windows XP.
Hope I am not giving you a bum steer.

---

### Post by klein de usa on 2007-02-25
hi
maybe it is because grub can't find it's menu list it is on the usb hdd ?
see grub is in the mbr of hdd and the menu list it looks for isn't there when the usb isn't pluged in, interesting problem,

---

### Post by eldeu on 2007-02-25
i understand grub is installed in the external hdd...

does not find it when its not connected... and i will not carry the external hdd around!!  :) 

i am thinking about re-installing ubuntu, the same way i did, except changing where the grub will be installed.

in he last step before installing ubuntu, it seems there is the option to install the grub somewhere else, because i read "GRUB will be installed to (hd0)"... any idea how to install it in the laptops hdd?

thankyou, once again

---

### Post by klein de usa on 2007-02-25
hi 
that will work , but there is a couple bumps:
grub has over written your mbr (master boot record)
you have to reinstall xp back into the mbr 
installing grub to partion on usb you need another boot program 
you might look into bootit ng just search it out in google and see if it will handle a usb drive i know it will handle grub because i use it, to boot 6 O.S.

---

### Post by eldeu on 2007-02-25
u right.

did it before reading your message, and in in the same situation... when usb hard drive isn't connected, the error appears.

do i have to re-install windows xp pack?

no other solution?

thanks

---

### Post by confused57 on 2007-02-25
> **eldeu said:**
> u right.

did it before reading your message, and in in the same situation... when usb hard drive isn't connected, the error appears.

do i have to re-install windows xp pack?

no other solution?

thanks
Here's a thread with someone who had the same problem:
[http://www.ubuntuforums.org/showthread.php?t=363306&page=5](http://www.ubuntuforums.org/showthread.php?t=363306&page=5)

You can reinstall grub to the external hd mbr, with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
your bios will need to be capable of booting to the USB drive before the internal hd.

You also need to restore your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
you'll need to do this to boot Windows, without the external hd connected

The Super Grub Disk(500 kb download) is able to boot Windows or Linux and can replace Windows mbr or Linux mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by eldeu on 2007-02-27
thankyou.

i have no floppy disc, but i hope i find a solution.

sure it works!

---

### Post by confused57 on 2007-02-27
> **eldeu said:**
> thankyou.

i have no floppy disc, but i hope i find a solution.

sure it works!

The Super Grub Disk is burned to cd...I believe there is a floppy & cd version.

---

