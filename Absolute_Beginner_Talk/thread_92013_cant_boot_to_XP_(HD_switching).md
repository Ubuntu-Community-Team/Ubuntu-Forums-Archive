---
title: "cant boot to XP (HD switching)"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by Scared on 2005-11-18
When i installed Ubuntu I unhooked one of my harddrives and plugged in another one because all of my IDE slots were full. So I install and everythings all good Ubuntu works and everything, but now when I decide to unhook my "linux" hd and plug my other one back in... i get this grub error 17. Im just wondering how i can get my copmuter to boot up without grub (so it goes back to Windows XP)

ive tryed switchin up the boot order, boot devices, and such things...i really have no idea what im doing...

EDIT: oh, one more thing, i can boot to XP when i have my linux hd in, sp im in XP right now....

---

### Post by Kyral on 2005-11-18
GRUB is setting on the MBR (Master Boot Record) of whatever was the boot drive (Whichever HD the BIOS looked for to boot from after the Floppy and CD drives) at the time of the Ubuntu Install. Now I don't know how your drives are setup, but if you want to load without GRUB you'd have to pull THAT drive. Perhaps more info?

---

### Post by wjp.reg on 2005-11-18
[QUOTE=Scared]When i installed Ubuntu I unhooked one of my harddrives and plugged in another one because all of my IDE slots were full. So I install and everythings all good Ubuntu works and everything, but now when I decide to unhook my "linux" hd and plug my other one back in... i get this grub error 17. Im just wondering how i can get my copmuter to boot up without grub (so it goes back to Windows XP)

ive tryed switchin up the boot order, boot devices, and such things...i really have no idea what im doing...

EDIT: oh, one more thing, i can boot to XP when i have my linux hd in, sp im in XP right now....[/QUOTE]

Don't be **scared** ;) 

Here's your answer: [http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp]("http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp")

**fixmbr** will do the trick

---

### Post by Scared on 2005-11-18
is there a  way in which i can access the MBR?

what kinda of 'more info' do you want to know?

EDIT: Thanks WPJ

---

### Post by Kyral on 2005-11-18
The MBR....its someplace that even I as cocky and how much I love to break stuff don't like to tread. By more info I mean like how your HDs are arranged (ie, what has Ubuntu on it, what has XP on it, etc)

---

### Post by Scared on 2005-11-18
thank you both so much

problem solved

im sure i'll be back soon however ;)

---

### Post by aberry7670 on 2005-11-18
Here's a way through Linux where you can copy the MBR and save it to a file. Not sure how your HDD's were at the time of install but if you can boot into Ubuntu then issue this command to copy the MBR (typically you would use the commands as root, but I have used it this way as well):

# sudo dd if=/dev/hda of=mbr.save bs=512 count=1

The file would be saved in your home directory. The /dev/hda is the first hard drive /dev/hdb is the second and so on. Make sure you have the right hard drive where you wrote the MBR at the time of installation.  With the above command you can save MBR written by any OS to a file and manipulate it to suite your needs.

Also, you can save this file in C:\mbr.save in windows and make an entry in your boot.ini like this: 

C:\mbr.save="Linux OS - Ubuntu"

What this would do is that if would link your Windows Boot Loder to the GRUB boot(that you saved as a file by using the above command) loader and allow you to toggel between the two to load the OS of your choice.

This command allows you to write the MBR on the HDD if you have saved it as a file.

# sudo dd if=mbr.save of=/dev/hda bs=512

here again the command is saying that write the MBR (mbr.save) to the HDD /dev/hda

Hope this information helps.

---

