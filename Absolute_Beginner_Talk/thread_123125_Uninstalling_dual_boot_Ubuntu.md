---
title: "Uninstalling dual boot Ubuntu"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by confounded on 2006-01-29
I know asking for this type of help is not liked. I am not disrespecting Ubuntu. I am sorry to ask for help in this. Please do not be angry. I do not mean to offend.

I have a dual boot computer, Ubuntu and Windows XP, using Grub. I need to remove Ubuntu and eliminate the dual booting, getting rid of Grub too.

Can anyone help me do this? I need clear instructions, please.

---

### Post by bartbes on 2006-01-29
don't actually know how to **remove** ubuntu, but I do know how to get back your normal booting.. (with winxp). Boot from the install cd and press 'r' (thought it was r) the recovery console. In the recovery console is a command to restore the boot sector. I'm going to search for the magazine I found it in post the command later

---

### Post by dueY on 2006-01-29
Boot with the Windows CD and go to the recovery console and type "fixmbr".  Then you can just format the Linux partition to NTFS or whatever you want.

---

### Post by confounded on 2006-01-29
I cannot boot my computer at all now.
I have lost it all. My XP will not now start.

I am sorry I asked.

---

### Post by confounded on 2006-01-29
Can I reinstall Ubuntu somehow and get my XP back?

---

### Post by randbag on 2006-01-29
Possiblities:
Find a boot floppy for Win 98, boot to it, and type: fdisk/mbr 
That should do it. If you can't find one, search the Web for a program that will make one for you.

Or go to [http://ultimatebootcd.com/](http://ultimatebootcd.com/) if you can and download it. Burn the cd and boot to that. In the menu you see after booting, select DOS/Linux boot disks, select the first one, and type the same command: fdisk/mbr .

There may be other ways, but either of these should work.

---

### Post by Herman on 2006-01-29
[http://users.bigpond.net.au/hermanzone/p18.htm]("http://users.bigpond.net.au/hermanzone/p18.htm")
Try reading the above link, that should help you. 

If you are in a hurry, and you have a 'System Rescue CD' handy, it has GAG bootloader on it which will boot Windows for you in an emergency (off the CD), or, if you choose, you can even install GAG to your MBR and it will be a good, easy way to fix your problem permanently, that's all you'll need to do.
For more GAG help: [http://users.bigpond.net.au/hermanzone/p12.htm]("http://users.bigpond.net.au/hermanzone/p12.htm")

You can also re-install Ubuntu and get XP back, but it isn't compulsory.
(Herman)

---

### Post by confounded on 2006-01-30
randbag,
I do not use Win 98. I cannot use fdisk /mbr. That is not for my filesystem type. 

Herman,
I do not want to use another bootloader. Ever. Especially one for Ubuntu. I do not ever want to be in this situation again. But I tried to reinstall Ubuntu. My XP is still not working. The partition is there.

---

