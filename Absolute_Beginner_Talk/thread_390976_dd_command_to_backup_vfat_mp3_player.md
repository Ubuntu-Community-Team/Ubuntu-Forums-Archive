---
title: "dd command to backup vfat mp3 player?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by civilmonkey on 2007-03-22
I have a new iAudio U3 mp3 player.  It's great but many many people have had problems with it becoming inoperatable after upgrading firmware or once the operating becomes corupt.  

I made backup copies of my MBR and parition table with the dd command when I was setting up Ubuntu / Win XP.  Am I able to do something similar with my mp3 player (FAT32).  My guess is that the firmware isn't accessible by dd, but hey, I thought I'd gather opinions.

How would one look at the parition to determine what values of 'bs' and 'count' to use with the dd command?

---

### Post by sad_iq on 2007-03-22
Why not make a copy of the entire content of the mp3 player? You must have a few Gigs in your /home folder don't you? Copy it, upgrade the firmware...if it works you can remove the image...if not you can replace the content of the mp3 player with the image saved by dd(should work in theory!!)...that way you don't even have to worry about *bs* and *count*!!!
 Also if you run low on disk space on your Hdd you can tell dd to make the image as a Gzip archive:
 **dd if=/dev/sda | gzip >/home/your_user_name/Mp3_backup.img.gz**
 To write the image to the player use: **gzip -dc /home/your_user_name/Mp3_backup.img.gz | dd of=/dev/sda**


.../dev/sda ...is the mount point for your usb player...and also ***_[COLOR="Magenta"]don't make any typo's[/COLOR]_***...or bad things will happen!!!

---

### Post by Yoooder on 2007-03-22
You have a good idea, but I don't think you can apply it in this case.

Firmware generally is a combination of software that is similar to a PC's BIOS, OS, and Applications all rolled into one.  Unfortunately, if the firmware is corrupted you lose the ability to speak with devices, and in turn the ability to restore any backups to the devices (at least without specialized equipment to extract and reflash the ROM chip.

---

### Post by sad_iq on 2007-03-22
Good point there *Yoooder*...that part slipped my mind :(

---

### Post by Yoooder on 2007-03-22
yeah, he should be able to backup the contents of the player with your commands, so at least he wouldn't lose any songs--but firmware itself is never as easy.

---

### Post by civilmonkey on 2007-03-22
Thanks folks,

I was pretty sure it wouldn't work but I thought I'd see if anyone else had tried it :)  

Cheers

---

