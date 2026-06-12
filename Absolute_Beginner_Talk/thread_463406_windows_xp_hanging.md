---
title: "windows xp hanging"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by jasepegg on 2007-06-03
i have just installed ubuntu 7.04 alongside my already installed windows xp pro.

ubuntu boots with no problems but windows xp refuses to boot from the grub menu and just hangs on a blank screen with the words "starting up...."
 
I just went through the ubuntu installation following the prompts and allowing an auto resize of my single windows partition...

here is the important info (i guess) from **[COLOR=DarkOrange]menu.lst [/COLOR]**.....

[COLOR=DarkRed][I]title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=ac3c9777-932d-4442-877a-60f5e1d92824 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=ac3c9777-932d-4442-877a-60f5e1d92824 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=ac3c9777-932d-4442-877a-60f5e1d92824 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=ac3c9777-932d-4442-877a-60f5e1d92824 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify        (hd0,0)
savedefault
makeactive
chainloader    +1
[/I][/COLOR]

i can still access my windows files as they are on a mounted drive in ubuntu but i still need to use some windows apps (unfortunately)..

please help!

---

### Post by ratman99uk on 2007-06-03
NOTE YOU WILL TEMPARLY LOSE UBUNTU DURING PROCESS

You could try restoring your windows xp master boot record. Boot from windows xp pro disk and select recover console you will then be ask for the administrator password for windows. Once you have done this you will have a dos interface, type:

"fixmbr"

this will ask you to confirm. Once you do this the pc will only boot windows. Your ubuntu partinion will still be there just not bootable. Assuming windows is fine, you will be able to resintall the GRUB boot loader from the ubuntu live cd.

- Ratman99UK

---

### Post by pappapump on 2007-06-03
Go back into Ubuntu and delete your swap file.
Restart then choose Windows and tap the F8 key to start up in safe mode.
Now do a scandisk on Drive C or whichever drive letter windows is on and it will tell you to restart to check your drive.
Click ok then restart to windows again and start up normally.
Let the scandisk run and it should reboot and make you a new swapfile as well as fixing your errors.
When windows FINALLY loads, you need to defrag right away, you'll find loads of fragmentation so it will take some time.
Now when it says would you like to view the logfile, click yes and make a note of the files that wouldn't defrag and navigate to them and see if theyre important.
If they are, then copy them to a new folder and delete the one they were in, unless theyre system files or Critical windows files.
If theyre disposable files then delete them and defrag again.
And that should do it, unless resizing stepped on critical boot files or system files.
In which case refer to ratman99's post.

---

### Post by jasepegg on 2007-06-03
how do reinstall the grub bootloader?

i cant see that option in the ubuntu disc menu

---

### Post by lamalex on 2007-06-03
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jasepegg on 2007-06-03
ran xp recovery console and reinstalled the mbr bootloader but windows (and now of course ubuntu) will not boot

i fear the ubuntu installation has done some serious damage to the windows partition...

recovery console saw the C:\windows installation but the fixmbr has not repaired the windows bootloader

i guess it now involves clean install of xp...i will then make the partitions myself before installing ubuntu...

you would think that this sort of error would be protected against....


cheers for any help

---

