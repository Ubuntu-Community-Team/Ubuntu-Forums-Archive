---
title: "Is it even possible to add mp3's to my palm"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by CameronCalver on 2006-08-15
hello i have a palm tx i can sync perfectly with my palm but i can only sync memo's how do i add mp3's

---

### Post by bhoughton on 2006-08-15
Do you have a SD card for your TX?  If so, MP3 files will be stored in the Audio directory on the card.  Your best bet for transferring them would be to pick up a cheap card reader (if you don't already have one), mount your SD card and copy them to that directory.  Afterwards, they will play fine with PocketTunes (in ROM) or one of the other music players.

Hope this helps.

Regards...

---

### Post by CameronCalver on 2006-08-15
yes but i have no plans to buy a sd card i was just going to add like 2 songs onto the internal memory

---

### Post by bhoughton on 2006-08-16
I currently believe that purchasing a SD card is the only way to handle MP3 files, as RAM will only hold PRC/PDB databases.  Cards are getting extremely cheap in price (128 MB ~ $15 / 512 MB ~ $30) and provide many benefits, such as storing native file formats DOC XLS PPT PDF MP3 OGG Video formats Native pictures, etc plus being a great way to backup the contents of your memory with the great free software NVBackup (definitely a good choice to have a backup if you have ever been stuck without one and needed a file or just had a hard reset).

---

### Post by CameronCalver on 2006-08-17
Ok well if that would be true how come when you get the palm it has 2 mp3's already on its internal memory?
And also i have got a sd card and i remember someone saying that there is a palm product that makes it so that the computer thinks that the sd card is a external device and mounts it can you remember what it is?
Also can someone tell me of a cheap sd card reader that works out of the box on linux 
thanx

---

### Post by djsroknrol on 2006-08-17
I bought a $20.00(US) USB card reader that worked out of the box...if your USB is working, it should read just fine...

---

### Post by click4851 on 2006-08-17
I would second that on the USB card reader, very slick.

---

### Post by bhoughton on 2006-08-17
The card reader is really the best way to go.  I picked mine up for around $20 USD and it works flawlessly with Ubuntu/other Linux distros.  It is a Lexar JumpDrive Treo.

The mp3's in RAM and specially encoded (I believe) and are installed from ROM each time the system loads (ie hard reset).  Unfortunately, RAM can't handle file formats other than PRC and PDB.

There is a program called CardReader from Softick ([http://www.softick.com/cardexport2/)](http://www.softick.com/cardexport2/)).  I haven't tried it so don't know if/how well it works with Linux, but since all it is doing is emulating a mass storage device, it should work.  There is a free trial so that you can test to see if it suits your needs.

Also, while you are at it if you use OGG files, you might want to install AeroPlayer from [http://www.aerodrome.us](http://www.aerodrome.us).  It will allow you to play OGG files for free, but will nag you if you install the MP3 library.

Hope this info is of use.  Let us know if you have any more questions.

Regards,
b

---

### Post by CameronCalver on 2006-08-18
ok i got card export and when i put in the card and get into to card export it says card:sandisksd512 i click connect but nothing comes up on the computer and im not sure if this is normal but if i do lsusb when card export is not running it says 
```
Bus 001 Device 004: ID 0830:0061 Palm, Inc.

```
but when it is running lsusb does not find anything?

---

### Post by CameronCalver on 2006-08-18
Yes i got it to work all i had to do was do a soft reset but for some reason it is read only how to i make it writable

---

### Post by CameronCalver on 2006-08-18
ok i did a sudo fdisk -l  and it said it was at sda1 so i put this in my fstab
```
/dev/sda1       /mnt/palm       vfat   umask=0000   0       0
```
 and then when i double click on it in nautilus it says only root can mount /sda1 at /mnt/palm so i did mount /dev/sda1 /mnt/palm and it said
mounting as read only then i can acess it but how do i make it not read only

---

