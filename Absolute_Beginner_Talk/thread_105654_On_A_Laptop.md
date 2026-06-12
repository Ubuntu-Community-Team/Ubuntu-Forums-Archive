---
title: "On A Laptop?"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by Kirt on 2005-12-18
Hi there!

I have been following news itemes about Linux for a few years now and have finally decided to give it a try. Why? Customobilty, security, and cost. But most of all, the desire to "get-my-hands-dirty" and dive into the "guts" of the operating sytem - basically to learn more about it from my very own mistakes!

I've browsed through this Forum for a couple of days now, trying to get a "handle" on what I want and what to expect from the Ubuntu OS. So far, evrything seems better than I expected and everyone appears to be very helpful!

I want to dual-boot, of course. Just in case things get sticky, I will need some way of getting online and back here for some help.

OK, Here is what I am working with:

Gateway 7422GX Notebook PC
Mobile AMD Athlon 64
2.21 GHz, 1.00 GB RAM
MS Windows XP SP2

What other information should I post that will help me out?

:-\"

---

### Post by akniss on 2005-12-18
From experience...  some things to keep in mind.

1) Ubuntu can't write to NTFS (The WinXP file system), so you may want to put a FAT32 partition on your drive to exchange files between OSs.  You can do this during the partitioning part of the Ubuntu install.

2) Think ahead about the sizes of your partitions for each OS.  Its much easier to do it right the first time than resize after its done.  (Although I've done it wrong and corrected it, so its possible.)

3) Install Windows 1st, and put GRUB on the MBR.

4) If you're installing on a preinstalled (factory) XP that you've been using for a while, then defragment, reboot, and defragment again before starting the Ubuntu install.

5) Backup your data before starting.

6) Put [www.ubuntulinux.org](www.ubuntulinux.org) in your XP browser's bookmarks.  You'll want to get back here early and often, especially if your wireless doesn't work right away, although I've seen lots of reports where there was no trouble whatsoever (mine included).

---

### Post by mistergq on 2005-12-18
I am using a Gateway 4525 GX Laptop.  The only problem I had was sound.  Other than that, I backed everything up, deleted all the temporary cache from my browser, emptied the recyling bin, then did a defrag, I booted the cd, I reduced the partion for XP, and created a partion for linux, and everything installed well.  

Highly recommend it!  If you have any questions, feel free to ask.

---

### Post by Gregory West on 2005-12-18
Hello, I too have a laptop I wish to load Linux Ubuntu 4. on. It is an old IBM notebook. First problem is that the disc is in the computer and I am stuck at the loading base data...it would not allow a partition either. Now I cannot get the disc out form the CD player???
IBM 2635JGU
Bus Clock 66 megahetz
64 Mbs Installed Memory
c:(FAT32 on drive 0)   
Local Drive Volumes: 4.98GB used and 2.45GB free
Windows 98SE (that I will eventually get rid of and use straight Linux when learned).
This computer will connect to the Internet with WiFi only.

Q: Should I remove Windows 98SE to gain hard drive space? Or should I wait until I learn how to use Linux first?
I tried loading the disc earlier but it was refused due to lack of space.

What are some of the things I should do before attempting another download of Linux.

---

### Post by Airspawn on 2005-12-19
[QUOTE=mistergq]I am using a Gateway 4525 GX Laptop.  The only problem I had was sound.  Other than that, I backed everything up, deleted all the temporary cache from my browser, emptied the recyling bin, then did a defrag, I booted the cd, I reduced the partion for XP, and created a partion for linux, and everything installed well.  

Highly recommend it!  If you have any questions, feel free to ask.[/QUOTE]

Whoa, you've got a 4525? I've got the 4540 myself. Arent these laptops great? Anyhow, did you ever get the card reader to work? I cant figure it out. If you're having problems with the volume, just go to the ASLA mixer and unclick "External Amplifier" under the "Switches" tab.

---

### Post by Kirt on 2005-12-19
[QUOTE=akniss]From experience...  some things to keep in mind.

1) Ubuntu can't write to NTFS (The WinXP file system), so you may want to put a FAT32 partition on your drive to exchange files between OSs.  You can do this during the partitioning part of the Ubuntu install.

2) Think ahead about the sizes of your partitions for each OS.  Its much easier to do it right the first time than resize after its done.  (Although I've done it wrong and corrected it, so its possible.)[/QUOTE]

Great! Thanks for the input! Now, the partitioning is taken place during installation of Ubuntu? Or is this something that I will need a seperate program for?

---

### Post by az on 2005-12-19
[QUOTE=Kirt]Great! Thanks for the input! Now, the partitioning is taken place during installation of Ubuntu? Or is this something that I will need a seperate program for?[/QUOTE]
You can do either, but I recommend using the installer for it.  Many windows partitioning programs do not handle linux file systems well.

The default behaviour for the installer is to see that you already have an OS installed and to offer to shrink down that partition to make room for ubuntu.  If you take this option, you will be asked how big to make your new ubuntu partition.  

That is as hard as it is.

The installer uses ncurses (text mode)  It works very well.  Do not be alarmed.

---

### Post by Kirt on 2005-12-19
Well, well, well... would you believe this: I cannot get my laptop to boot the install disk! Even after setting the BIOS to start from the CD ROM drive!

Any suggestions? :confused:

---

### Post by etc on 2005-12-19
^^
You burned the iso as an image, not a data disk right?  Try burning at a slower speed.

Time for advice
Put your /home on a seperate partition.

You're going to have to mess around with the mixer to get your sound to work, it seems a lot of Gateway users have the sound problem, but I just reinstalled breezy and it worked right away.

Your wireless card won't work without ndiswrapper, so read up on that before you install it.

Good luck.

---

### Post by akniss on 2005-12-19
[QUOTE=Kirt]Well, well, well... would you believe this: I cannot get my laptop to boot the install disk! Even after setting the BIOS to start from the CD ROM drive!

Any suggestions? :confused:[/QUOTE]

Where did you get your CD?  Download and burn? Shipit? From a friend?  

When you try to boot from the CD what happens?  does the system hang? does it just ignore the disk and boot into windows?

---

### Post by Kirt on 2005-12-20
[QUOTE=akniss]Where did you get your CD?  Download and burn? Shipit? From a friend?[/QUOTE]

Downloaded & Burned it

[QUOTE=akniss]When you try to boot from the CD what happens?  does the system hang? does it just ignore the disk and boot into windows?[/QUOTE]

Ignores the disk and boots into Windows

---

### Post by Kirt on 2005-12-20
[QUOTE=etc]^^
You burned the iso as an image, not a data disk right?  Try burning at a slower speed.

Time for advice
Put your /home on a seperate partition.

You're going to have to mess around with the mixer to get your sound to work, it seems a lot of Gateway users have the sound problem, but I just reinstalled breezy and it worked right away.

Your wireless card won't work without ndiswrapper, so read up on that before you install it.

Good luck.[/QUOTE]

Thanks! I will burn another CD at a slower speed and look into ndiswrapper this evening :)

---

### Post by az on 2005-12-20
[QUOTE=Kirt]Downloaded & Burned it



Ignores the disk and boots into Windows[/QUOTE]

Did you put the file onto the cd?  When you look at the cd in windows do you see just the iso file?  because it is a cd image.  You have to make a cd out of that image.  You should see a whole directory tree when you view the contents of the cd you make.

---

### Post by Kirt on 2005-12-20
[QUOTE=azz]Did you put the file onto the cd?  When you look at the cd in windows do you see just the iso file?  because it is a cd image.  You have to make a cd out of that image.  You should see a whole directory tree when you view the contents of the cd you make.[/QUOTE]

Yes, there is a directory tree visible on the CD.

---

### Post by Kirt on 2005-12-20
Tried installing with slower burned CD.

When the computer started it accessed the CD ROM drive first and it worked for about 10 seconds (CD led flashed with a whirring sound). Then went right on to load Windows.

This is getting a bit frustrating - not being able to even start! ](*,)

*But, if you all will bear with me, I'm willing to stick to it!*

---

### Post by az on 2005-12-20
[QUOTE=Kirt]Tried installing with slower burned CD.

When the computer started it accessed the CD ROM drive first and it worked for about 10 seconds (CD led flashed with a whirring sound). Then went right on to load Windows.

This is getting a bit frustrating - not being able to even start! ](*,)

*But, if you all will bear with me, I'm willing to stick to it!*[/QUOTE]

Is your bios set to boot the cdrom first?

---

### Post by invisage01 on 2005-12-20
If your doubtful... try the LIVE CD... works a treat on most systems!!! :D

make sure your BIOS is set to boot from CD-ROM before HD's! :)

cheers

- i.

---

### Post by Kirt on 2005-12-20
Yep! BIOS is set to CD first.

*Wierd, huh?!*

---

### Post by Kirt on 2005-12-20
Well, I Burned yet another CD... and I made sure it was an ISO image, not a data cd.

Restarted laptop, confirmed that the BIOS is set to CD ROM first, restarted again, computer accessed the CD ROM Drive for a moment (light blinked several times), then proceeded to load XP.

I am now at a loss as to what I should do next... :confused: 

*(Note: I did try the Live CD with the same results.)*

---

### Post by scole on 2005-12-20
Kirt i will save your skin, I had the same problem. The bios will not boot from the drive so you need a boot disk that will let you choose what you want to boot off of. If you have a floppy drive go here [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm) and download the sbootmgr.dsk image then download from this site [http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm](http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm) . . . rawwritewin-0.7.zip. Unzip and write the image to floppy using rawwrite you will have to display all types of files when you go to write although it isnt seen as an image it will work. 
Once that finishes go pop that into the floppy drive setup Bios to boot off floppy and you then put in the Ubuntu cd. The hit tab and go to refresh partions to be safe. then select cd-rom from the menu there. It should boot right up into the install program. If you have problems with the partions make and extra partion ahead of time and then go in the setup again when the partioner loads delete the partion you made for ubuntu from the menu and then hit enter on free space. tell ubuntu setup to automaticly setup the free space then youre good to go. tell me if this works :)

---

### Post by etc on 2005-12-20
I had a problem with my old Dell laptop where it wouldn't boot from ANY cd I burned myself.  I tried different speeds, computers, and media.  NOTHING WORKED, except the Ubuntu cds from shipit, so give that a try if all else fails.

---

### Post by Kirt on 2005-12-20
[QUOTE=scole]Kirt i will save your skin, I had the same problem. The bios will not boot from the drive so you need a boot disk that will let you choose what you want to boot off of. If you have a floppy drive go here [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm) and download the sbootmgr.dsk image then download from this site [http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm](http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm) . . . rawwritewin-0.7.zip. Unzip and write the image to floppy using rawwrite you will have to display all types of files when you go to write although it isnt seen as an image it will work. 
Once that finishes go pop that into the floppy drive setup Bios to boot off floppy and you then put in the Ubuntu cd. The hit tab and go to refresh partions to be safe. then select cd-rom from the menu there. It should boot right up into the install program. If you have problems with the partions make and extra partion ahead of time and then go in the setup again when the partioner loads delete the partion you made for ubuntu from the menu and then hit enter on free space. tell ubuntu setup to automaticly setup the free space then youre good to go. tell me if this works :)[/QUOTE]

This sounds like such a wonderful idea!

But there is a bit of a problem: This laptop does not have a floppy drive :-k

However, I will note what you have suggested for future (I hope there is one) reference.

---

### Post by Kirt on 2005-12-20
[QUOTE=etc]I had a problem with my old Dell laptop where it wouldn't boot from ANY cd I burned myself.  I tried different speeds, computers, and media.  NOTHING WORKED, except the Ubuntu cds from shipit, so give that a try if all else fails.[/QUOTE]

hmmm.... could be the answer.

Thanks!

---

### Post by Kirt on 2005-12-21
Well, I tried to make a boot CD using Nero. It booted fine and I was able to access the Ubuntu files on the CD.

However, when I try to read anything on the disk or run the install program it tells me that it is an unrecognized type of file. (Will not run it.)

I was able to access the Gateway "safe" drive. But it seemed all I could do was browse - not touch! LOL

This has been an interesting, yet frustrating experience. As much as I would love to install and get into Ubuntu, it looks as though I may just have to 'suffer' with XP :-({|=

Thanks for all of your suggestions and for trying to help!

Hopefully I will be back soon with some good news! (For a change!)

---

### Post by Kirt on 2005-12-22
Running Ubuntu through VMWare (trial)

Does not have all the "bells & whistles" I'm syre and I don't know how far I trust it seeing how I am running it under Windows... but, at least I get to try it for awhile!

---

### Post by Kirt on 2005-12-24
**Are you all ready for a good laugh?!**

Well, I finally figured out what I was doing WRONG:

When I downloaded the Ubunto ISO it appeared on XP as as WinRAR zip file. Soooo, I thought I had to unzip the file before I burned it. Well, many of you, I'm sure are now smiling and shacking your heads!

Just out of curiosity I burned the file (without opening it) with Alcohol 120% slapped it in the CD ROM drive, rebooted and BINGO!!!!!! It works!

Right now I am running Kubuntu (hey, I like blue better than brown! LOL)

Anyways, I really happy with the choice so far... even though I accidentaly wiped XP of the system :oops:

All I have to do is get the wireless running???

---

### Post by akniss on 2005-12-24
Too bad about your XP...  It wa probably time for your annual reinstall anyway right???  :D    Here's hoping you won't miss it and never look back!

---

