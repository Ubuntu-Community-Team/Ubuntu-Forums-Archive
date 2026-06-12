---
title: "How boot without grub rescue into Windows 7 without cd reader"
date: 2013-03-02
forum: Any Other OS
---

### Post by Nevrosi on 2013-03-02
Excuse me but i have a big problem that i can't solved BY reading old posts: i have a notebook with Windows 7 . I wanted to install ubuntu so i make a partion of disk e with unetbootin installed on a USB i installed ubuntu but it didn't run. So i run Windows and like a big big idiot i dealloc the partion where there was ubuntu to try another way. So i discover this error . Grub no such partion grub rescue.  I don't know what can i do to run Windows (and even i will run Windows i don't know how to repair ) or to reinstall ubuntu BY unetbootin. Please help me . I don't have much experience as you se.

---

### Post by Nevrosi on 2013-03-02
Sorry the title is wrong it is 'with' not without!

---

### Post by coffeecat on 2013-03-02
@Nevrosi, you posted in Forum Feedback & Help which is for help with using the forum. I've moved this into Other OS because, at the moment, this is a Windows problem, albeit caused by removing Ubuntu.

By deleting the Ubuntu partition, grub (the Ubuntu bootloader) in the mbr is looking for the rest of itself in the Ubuntu partition, which is no longer there. You need to re-install the Windows mbr if you need to boot into Windows before trying to re-install Ubuntu. What you need should be on this community documentation page:

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by Nevrosi on 2013-03-02
Oh I'm sorry i post in the wrong place. But i read in your link but there you must have a cd or DVD reader and i didn't have it!

---

### Post by coffeecat on 2013-03-02
If you look at the methods under "How to partially fix the Windows bootloader using an Ubuntu CD" you can do these using a live Ubuntu USB as well.

---

### Post by mips on 2013-03-02
If you still have ubuntu on the usb stick you can reinstall it and it will reinstall grub for you which will allow you to boot with Windows. If you have the Windows ISO image then you can create a bootable install media with the Windows USB download tool [http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool](http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool) boot from it and select the repair option to reinstall the windows MBR. Now you can delete the windows partitions.

---

### Post by Nevrosi on 2013-03-03
ok thank you very much i managed. but now i have another big problem. when i install ubuntu go all ok but than my ubuntu didn't run correct. i show how i install ubuntu maybe you can give me a hand :). I partioned my hard disk with windows tools. i reduce the volume of my disc and keep the partion i want to install ubuntu dealloc. than i run boot by unetbootin and install all correct but ubuntu isn't open. how can i do?

---

