---
title: "Problem installing Ubuntu 18.04 on MacBook Pro (8,3) Late 2011"
date: 2018-09-22
forum: Apple Hardware Users
---

### Post by bigdip2 on 2018-09-22
Hello,

First, I would like to say Hi!, this is my first post.

Now my problem


I would like to install Ubuntu on my MacBook pro 2011 (8.3)

- Intel Core i7
- 16 GB Ram
- 1 TB HD (this is where I want to install Ubuntu - the disk has been partitioned so I have OSX High Sierra + an MS-DOS FAT partition for Ubuntu (400 GB)).
- 1 TB SSD

I followed this tutorial ([http://www.applegazette.com/mac/how-to-install-ubuntu-and-dual-boot-macos/](http://www.applegazette.com/mac/how-to-install-ubuntu-and-dual-boot-macos/))

This is what I did:


I partitioned my HD disk (MS-DOS FAT), I disabled SIP, I installed refind, I have Ubuntu 18.04 on a USB key.

The problem:

At the time of installation I get this error:


MODSIGN: Could not get UEFI db list

I'm a complete noob when it comes to Linux, but I want to learn.


Can you help me ?


Thank you in advance,


Tom

---

### Post by bigdip2 on 2018-09-25
Anyone?

---

### Post by oldfred on 2018-09-25
I do not know Mac.
But you should be using gpt partitioning. And Linux only uses a FAT32 for the ESP - efi system partition which I thought your Mac already has.
And the Linux partition has to be ext4 or other Linux type formats.

Your USB flash installer also is FAT32.

       Install to Mac
[https://ubuntuforums.org/showthread.php?t=2365454&p=13663640#post13663640](https://ubuntuforums.org/showthread.php?t=2365454&p=13663640#post13663640)
[URL="https://help.ubuntu.com/community/MacBookPro"]https://help.ubuntu.com/community/MacBookPro
      [/URL]
 FAT32 format  & label with boot flag on Mac
[URL="https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation"]https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation
      [/URL]
 EFI-Booting Ubuntu on a Mac
[URL="http://www.rodsbooks.com/ubuntu-efi/"]http://www.rodsbooks.com/ubuntu-efi/
[/URL]
 [http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 

  MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html) 
        [URL="https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation"]
[/URL]

---

### Post by bigdip2 on 2018-09-26
[COLOR=#DD4814][COLOR=#C61919][/COLOR][/COLOR]Thank you for your reply! I really appreciate your help!

I will consult all the links and try again.

Bestest,

Tom

---

### Post by kevin160 on 2018-09-29
Does your AMD graphics chip still work properly?  Many 2011 mbps have bad chips and you may need to force it to use the Intel 3000 graphics instead.  See [this thread]("https://ubuntuforums.org/showthread.php?t=2157775").

---

### Post by bigdip2 on 2018-10-01
[COLOR=#DD4814][COLOR=#000000]@[kevin160]("https://ubuntuforums.org/member.php?u=1977979") Yes, my AMD graphics chip works, the whole MB was replaced under extended warranty last year. [/COLOR][/COLOR]

---

### Post by kevin160 on 2018-10-01
Nice.  Unfortunately, those replacement boards all fail eventually, so make sure you're running your laptop's fans a little higher than normal so your new GPU doesn't melt itself like the old one did.  I use the macfanctld package on Ubuntu for this, and I have set fan_min: 3000 in my /etc/macfanctl.conf file.  It's not too loud on my 8,2, but it is audible in a quiet room.

---

### Post by compa3 on 2018-11-11
Hola Tom, encontraste la solución tengo la misma mac y no me deja entrar se queda la pantalla en blanco estoy intentando instalas el ubuntu y nada

---

