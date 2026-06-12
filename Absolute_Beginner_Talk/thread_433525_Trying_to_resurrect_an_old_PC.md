---
title: "Trying to resurrect an old PC"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by _F1 on 2007-05-05
I've been reading about Linux lately, and I decided I would try and resurrect an old PC of mine that is currently running Win98 SE, but is horrendously slow and has basically become almost unusable.

Xubuntu seems like the perfect OS for my purposes, so I went ahead and downloaded the ISO and burnt it onto a disc. I have gone into the Settings and set the Boot Order to CD > Floppy > HDD, but every time it doesn't seem to recognise the disc, and boots to Win98, and I can't work out why. There are no apparent error messages. It works perfectly on my newer (though still old) WinXP PC.

The PC is a Compaq, and has 192.0 MB (upgraded from the original 32MB). If you need anymore information I will try and find out.

I'd prefer to run off a CD at first, before installing onto HDD.

---

### Post by bullgr on 2007-05-05
does the cd device work properly?
try in winblows 98 to put your burned ubuntu cd.

it's autostarting? can you see the contents of the cd?
if the two questions above are no, then you have problem with the cd device.

or like we say in my country, it's given the spirit... O:)

---

### Post by orange2k on 2007-05-05
You need a bootable CD-ROM and you have to modify the settings in the BIOS to boot from this CD-ROM first.

---

### Post by _F1 on 2007-05-05
CD drive works; I can see the contents of the CD.

The BIOS settings are set in the order I mentioned in first post: CD > Floppy > HDD.

I would assume the CD is bootable considering it boots on my WinXP PC?

---

### Post by orange2k on 2007-05-05
What I meant is that your CD-ROM drive has to be bootable - not all CD-ROM devices are...

---

### Post by _F1 on 2007-05-05
Is there a way to find out (apart from trial-and-error)?

---

### Post by orange2k on 2007-05-05
If you have WIN98 up and running you can create a rescue floppy disk (I believe its called something like that). With it you can startup your system (DOS with enabled CD-support) and THEN boot the CD manually...I also believe that you can start the system with command-promt with CD-support enabled before your system boots to WIN98 by pressing F4 (or some other F button - not sure anymore cause I haven`t used WIN98 in quite a while)

Not sure if it would work for you, but you can try...

---

### Post by _F1 on 2007-05-05
I can't find any suitable information on rescue floppy disks.

---

### Post by orange2k on 2007-05-05
Look here: [http://www.techadvice.com/W98/S/Startup-Disk_w98.htm](http://www.techadvice.com/W98/S/Startup-Disk_w98.htm)

---

### Post by bullgr on 2007-05-05
go there
[http://www.bootdisk.com/](http://www.bootdisk.com/)
download win98 boot disk image and write it in a black floppy disk

and follow the instructions orange2k give...

but it's weird that the cd device can't boot... how old is the device?
and what for device is it?

---

### Post by orange2k on 2007-05-05
I found something usefull on the ubuntu CD that might help you - it`s in the "install" directory:

About the Smart Boot Manager image
----------------------------------

  The file `sbm.bin' that is available in this directory may be useful
  to you if you are not able to directly boot the first CD because your
  BIOS may be too old and may not support ISOLINUX.

  Then, instead of booting on the CD directly, you create a Smart Boot
  Manager floppy image by using the sbm.bin disk image. You can create this
  floppy with rawrite (under DOS) or with dd (under Linux). Now you can
  boot on this floppy disk and it will detect your CDROM and let you boot
  on it bypassing any BIOS limitation.

What is SBM ?

  Smart Boot Manager or briefly SmartBtmgr (SBM), is an OS independent
  Boot Manager - a program that is loaded by the bios before any
  operating system and allows you to choose which operating system to
  boot.

  SBM is included in Debian in two ways, the package bmconf allows us to
  install and configure an old version of SBM and sbm wich is the latest
  version of SBM with an installer.

What's the use of SBM on the CD then ?

  SBM includes an IDE driver that allows us to boot the cds even on
  machines with a BIOS that wouldn't support booting from CD, provided our
  CDROM is an IDE one, that is, so you can make a SBM floppy and boot from
  it and then tell it to boot from your CDROM.

  Also, there are some cases where the BIOS would allow booting from the CD
  but isolinux fails to boot from there, in this case you can either boot
  using a CD other than the first, as the others don't use isolinux, or you
  can make a SBM floppy and boot from this floppy and then tell SBM to boot
  your CDROM.

How do you make a SBM floppy ?

  If you have SBM installed on a box you can run sbminst. Otherwise you can
  put the sbm.bin floppy image that we provide with our cds onto a floppy
  just like you would do with a rescue image.

---

### Post by Palypup on 2007-05-05
You can make a boot disk by going into >settings  >add remove software and when it loads there are three tabs at the top. I believe it is the center tab for windows programs and in there is the option for a boot disk. But I don't believe that will allow you to do what you want to do..

---

### Post by Palypup on 2007-05-05
Orange2k's smb sounds like your best bet.

---

### Post by orange2k on 2007-05-05
If you can`t figure out how to write this bin file  to a floppy, here`s what I would do (on XP):

first go here: [http://sourceforge.net/project/showfiles.php?group_id=4185](http://sourceforge.net/project/showfiles.php?group_id=4185)

download file: sbminst.exe

start cmd.exe

put in an empty floppy disk to your floppy drive and then go to the directory you downloaded the file to and then type: sbminst.exe -d 0

---

### Post by _F1 on 2007-05-05
Got the boot disk working, there are a number of options but none that explicitly mention booting from CD. There is a command prompt option -- is this the appropriate method, and what do I type in the command prompt?

EDIT: I didn't notice the second page of replies, I will try the SBM, too.

---

### Post by orange2k on 2007-05-05
I`m sorry about the confusion with the win98 startup disk if it doesn`t work...
I should have posted the thing about SMB first, but I didn`t know about it myself until I did some research (just in case I have a similar problem to yours)...:)

---

### Post by _F1 on 2007-05-06
I made the SBM disk, and booted to it fine. In the menu I scrolled down to CDROM and pressed Tab for options (don't know if this is correct, Enter saves [saves what?]). In the Options, I went down to Boot it! (again, no idea if this is right) and pressed Enter, and the PC appeared to freeze.

I can't really find any instructions on how to use SBM through Google.

Is it worth looking into the Win98 startup disk and using the command prompt? (How?)

---

