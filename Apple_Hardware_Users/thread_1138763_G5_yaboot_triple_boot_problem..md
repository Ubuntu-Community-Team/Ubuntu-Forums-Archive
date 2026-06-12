---
title: "G5 yaboot triple boot problem."
date: 2009-04-26
forum: Apple Hardware Users
---

### Post by casbahdk on 2009-04-26
I have two internal HDs in my G5. /dev/sda with OS X and Ubuntu 8.04 installed and /dev/sdb with an install of Kubuntu 9.04 Jaunty. I think the yaboot.conf file is OK, but I still only get to choose from Linux, OS X or CD in the startup menu item. Ubuntu 8.04, which isn't in the list resides at /dev/sda4.

Here is what my yaboot.conf file looks like:

```
boot=/dev/sda2
device=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@1/disk@0:
partition=3
root=/dev/sdb3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sda3

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/sda4.
image=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:4,/boot/vmlinux
    label=sda4-Linux
    root=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:4
    append="root=/dev/sda4 ro quiet splash"
    initrd=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:4,/boot/initrd.img

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/sda4.
image=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:4,/boot/vmlinux.old
    label=sda4-old
    root=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:4
    append="root=/dev/sda4 ro quiet splash"
    initrd=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:4,/boot/initrd.img.old
```

Cheers

---

### Post by tiresia on 2009-04-26
With yaboot you have two prompt, at the first one you can choose the OS (linux, macosx, cd...) at the second prompt you can choose which linux you want to boot from. To see the different gnu/linux systems installed on your computer, hit TAB at the second yaboot prompt.
For more infos on yaboot see [http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)

---

### Post by casbahdk on 2009-04-27
> **tiresia said:**
> With yaboot you have two prompt, at the first one you can choose the OS (linux, macosx, cd...) at the second prompt you can choose which linux you want to boot from. To see the different gnu/linux systems installed on your computer, hit TAB at the second yaboot prompt.
For more infos on yaboot see [http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)

OK, thanks for the info. I didn't realize that the idea was to switch between Linux versions at the second prompt, but now I realize that it is quite logical. Here is what my revised yaboot.conf file looks like:

```
# Color Settings
fgcolor=black
bgcolor=yellow

# Where's the bootstrap partition
boot=/dev/sda2
device=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@1/disk@0:
partition=3
root=/dev/sdb3
# How long to wait at the OS boot menu (seconds)
timeout=100
install=/usr/lib/yaboot/yaboot
# CHRP script spec
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

# to boot OSX by default
# to boot linux by default, change to defaultos=linux
defaultos=macosx

macosx=/dev/sda3

image=/boot/vmlinux
	label=Kubuntu
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/sda4.
image=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:4,/boot/vmlinux
    label=sda4-Ubuntu
    root=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:4
    append="root=/dev/sda4 ro quiet splash"
    initrd=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:4,/boot/initrd.img

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/sda4.
image=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:4,/boot/vmlinux.old
    label=sda4-old
    root=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:4
    append="root=/dev/sda4 ro quiet splash"
    initrd=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:4,/boot/initrd.img.old
```

---

### Post by tiresia on 2009-04-27
As you did, you can customize yaboot according to your needs and wishes. Of course, you don't need to keep 'sda4-', you can just use the label Ubuntu - but maybe you prefer like this. 
Do not forget to run 'ybin -v', when you change yaboot.conf And make a backup of yaboot.conf - you can always need it again
With other different GNU/Linux distros, such as Fedora, yaboot works slightly different.
Please, mark this thread as solved, if everything works for you.

Btw, I do really like how kde is working now on ppc - and it's great that also ppc's users have live CDs for ubuntu, kubuntu and xubuntu!

---

### Post by casbahdk on 2009-04-27
Yes, I went back and made the labels even simpler. OpenFirmware seems to insist on using US key mapping regardless of the keyboard being used. I got tired of hunting around for the "-" hyphen mark, so I decided to keep it simple.

Which reminds me, why has there never been any attempt to map the keys for Apple keyboards to the keyboard language AND keyboard type (white, aluminum, etc.) during the Ubuntu installation?

My miniscule beef aside ;-) yes, I am pleasantly surprised about the effort exerted by the community to provide a wide range of 'buntu versions to choose from for the PPC platform. Just color me happy :-))

I was starting to get worried that the end was near with regards to PPC support and that we all would have to migrate to Debian or Fedora.

I hope that the effort continues for a long time as 'buntu is my favorite distro.

Cheers

---

### Post by tiresia on 2009-04-27
> **casbahdk said:**
> Yes, I went back and made the labels even simpler. OpenFirmware seems to insist on using US key mapping regardless of the keyboard being used. I got tired of hunting around for the "-" hyphen mark, so I decided to keep it simple.

Which reminds me, why has there never been any attempt to map the keys for Apple keyboards to the keyboard language AND keyboard type (white, aluminum, etc.) during the Ubuntu installation?

In the Danish Keyboard, you find the sign "-" typing "+" (the key where you have "?" or "+")

---

### Post by casbahdk on 2009-04-27
Thanks. The biggest problem that I have is trying to get the CD eject button to work in Kubuntu. I am using an aluminum Apple keyboard with number pad.

---

### Post by tiresia on 2009-04-27
You can always use ```
eject
eject -t
``` till you find the solution

---

