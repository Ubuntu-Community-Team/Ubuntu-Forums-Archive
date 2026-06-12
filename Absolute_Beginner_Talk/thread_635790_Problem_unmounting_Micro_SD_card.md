---
title: "Problem unmounting Micro SD card"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by cool_penguin on 2007-12-09
Hi Guys,

I have been working on my Apacer Micro SD card for the past 2 days and no success yet. I recently bought an Apacer Micro SD Card (1GB) for my Motorola KRazr K1 Cellphone. When i plug the device using a usb cable, the card auto-mounts and it fires up Rhythm box  automatically and i am able to copy files, delete files, etc. 

The problem comes when i try to eject the media using the right click. When i right click the mounted icon (icon looks like an iPod icon), and click on Eject, i get a bubble message towards the bottom right of the screen saying, still writing to disk, Please wait, bla, bla , bla, etc. 

Then i get a window saying that cannot eject media. 

Sometimes, the media gets ejected (evident from the disappearance of the mounted icon), with the bubble message as mentioned above. But then in a few seconds, it gets mounted again and fires up Rhythm box. 

The only thing that seems to work is the command line where in i type in 

sudo umount /media/SANVOL (The latter is the name of the volume)

When i plug in my old Transcend 128 Mb USB drive, it is identified as a USB Mass storage device (Evident from the USB emblem above the icon) and i am able to unmount it successfully. 

I am wondering why my Micro SD card is not recognised as a USB mass storage device. When not yet mounted, it has an icon of a regular hard drive in Nautulis. 

Can anybody please help me. I have been looking all over the forums and google for help, but no success. I am wondering if there is a problem with Apacer. 

Also one thing that i would like to mention is that, i had the same problem with a 512 Mb  MP3 player. I would get, exactly the same problem as above mentioned. Anyways, i have given away that player to a friend. 

One post on the forum said that i should try 

sudo rm /media/.hal*

But even that does not seem to help. 

Any help from you guys will be greatly appreciated.

---

### Post by cool_penguin on 2007-12-09
I forgot to mention, I am using Ubuntu Gutsy 7.10

---

