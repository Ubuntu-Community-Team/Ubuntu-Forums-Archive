---
title: "[SOLVED] XP Folders"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by HanaD on 2006-10-28
HI friends,

I have a daul operating system, with Ubuntu6.06 LTS and win xp installed,
i have recently installed Ubuntu and am new to linux,
i have partitioned my hard disk such that one partition(10 gb) has xp, the other(10gb) has linux and the 3rd partition i use for data storage purpose(Data volume)...which is NTFS formated,

now can any one help me out, i want to acess XP folders from linux,
can i use that data when i am logged on to linux??
i can see the data volume when i log on to linux in the location PLACES---COMPUTER, but can not open it, get an error message..Unable to mount the selected volume.
error: device /dev/hdb4 is not removable

error: could not execute pmount


Please help!

Regards,
Hana Dhillon.

---

### Post by jamyskis on 2006-10-28
Drives with XP on them are usually formatted with NTFS, which Ubuntu 6.06LTS can't access without root permissions. 6.10 for the record, is the first release that *can*, but think very carefully about stability issues before rushing in to upgrade.

You do have a way of getting around this under 6.06, if you just want to access your files to copy them over.

I doubt that /dev/hdb4 is your XP drive, as hard drives are usually mounted under /dev/hdc, or /dev/hdd if you have a second drive installed. Call up a terminal go to the folder /media - a series of links are provided by the installer so that your existing drives can be mounted - do you see anything beginning with hdc or hdd?

If so, call up a root terminal with "sudo bash" and entering your password.  Then try and enter the directory and ls it to see if it's the right one. Remember - you shouldn't be in with root privileges longer than necessary, so close it when you're finished.

If you're not so keen on the command line (you really ought to get acquainted with it, but it's not always necessary) then you can do the same stuff from Nautilus by pressing ALT+F2 on the desktop and typing "gksudo nautilus" and doing the same as above. Again, remember to close it when you're finished.

Oh, by the way - before closing the root Nautilus/shell, remember to set the permissions to the files you copied so that you don't need root access to read them. You can just do this while in a root shell by going to your home directory and typing "chown <your user name> ./<the file name>".

Hope this helps!

---

