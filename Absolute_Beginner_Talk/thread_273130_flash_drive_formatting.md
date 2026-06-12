---
title: "flash drive formatting"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-10-07
I just got a new PNY Attache flash drive. When I plug it in it is recognized by Ubunutu but I can't mount it and I can't figure out how to format the drive. Does anyone know how to get it working on Ubuntu. It is a new flash drive right out of the box. I am using Ubuntu Dapper Drake. Thank you for any help.

---

### Post by matthew on 2006-10-07
There are many ways to do this. This one is one of the easiest.

You can install a program called Gnome Partition Editor which will allow you to format the flash drive.```
sudo apt-get install gparted
```The program will appear in your menu at System->Administration->GnomePartitionEditor

Plug in the drive and run the program. At the upper right is a drop down menu that will let you select all the detected drives on your system. [COLOR=Red]Make sure you select the flash drive, NOT your hard drive.[/COLOR] 

Then select Partition->Unmount to make sure the flash drive in not mounted. Then select Partition->FormatTo->Fat16

That will make it readable on a Mac, Windows or Linux machine.

Good luck!

---

### Post by grim918 on 2006-10-07
I have gparted installed. I tried using it before I posted but I can't mount the flash drive so when I use gparted it doesn't even show up in the drop down list. I tried mounting the flash drive by going into Places->Computer and double clicking "USB Disk 28X" which is the default name given to the flash drive. I get an error saying that the device was not able to mount. I tried to format the drive on a windows box and still I can't get it working. Is there a chance that the flash drive has a defect. Thank you for your help.

---

### Post by grim918 on 2006-10-08
Does anyone have any idea what I am doing wrong with this. It seems that no one knows anything. I have searched google and the forums but no one has a problem like mine. I can't format the drive on windows or linux.

---

### Post by matthew on 2006-10-08
The drive needs to be UNmounted for gparted to be able to partition it...however it sounds to me like the hardware has failed and the drive is bad.

---

### Post by matt_risi on 2006-10-08
I use a flash drive and never had to reformat it, it still uses FAT from when I had Windows on this computer (recently whiped out Windows partition). Proud to say I'm running a full Ubuntu laptop right now! :)

I'd submit a bug report with full details on model and any messages recieved, I don't think the problem is with the drive.

---

### Post by matthew on 2006-10-08
I have had to reformat drives that have seen a lot of use. The flash ram doesn't work forever. I had one that I used on Windows years ago and it worked fine on Ubuntu for a long time as well. Then one day I deleted everything from it but the memory never showed clear. The drive said nothing was on it but also that there was no space free. I formatted as I described above and it worked great for a long time again...then one day it just died. I've used some that needed reformatting about every 10th time it was mounted and others that never needed it. All in all, though, I don't know if I've ever had one last more than a few thousand mounts without having some sort of problem, some that were reparable and others that weren't.

---

### Post by pistcivet on 2006-10-08
You could try formatting with the command line:```
sudo mkfs.msdos -F 32 /dev/sda1
```If you have a SATA HD, use sdb1.
Two SATA drives, use sdc1. (I am not responsible if you format the wrong drive)

Try: apropos mkfs
and
man mkfs.msdos
for more information.

---

### Post by grim918 on 2006-10-10
I haven't had access to the forums because my internet connection is down since I just moved to a new house. I ended up just getting myself a new drive. I got rid of the old one. I just got stuck with a bad one. Thank you for the help.

---

### Post by fedupwithwin on 2006-10-10
Uh, excuse me....  Many people have been having problems getting perfectly good USB drives to mount properly.  If you want proof of this statement, please do a forum search using the keywords "memory stick", "pen drive" or "USB memory".  By looking/reading about the sheer number of people with this same sort of problem, I believe we can conclude that there is a bug in Dapper that no one has figured out yet.  I have a perfectly good USB drive - works fine in XP but will not mount properly in Ubuntu.  I've made a few posts to this effect but, have not gotten any decent responses.  I have a decent amount of experience in various types of low-level programming and would be more than willing to run any tests requested and post the results.  Can somebody please point me in a reasonable direction here?

---

### Post by redDEADresolve on 2006-10-10
i'm not an expert but I had the same exact problem. then i just tossed my drive into a windows xp pc and formatted it there. worked flawlessly afterwards & its been running good for weeks. sometimes the easiest solution is the best plus it was easier for me to rename it in windows.

you can find a windows pc with a usb drive just about everywhere, ie take it to microcenter, bestbuy, circuit ciry, etc

---

### Post by Trickyphillips on 2006-10-11
> **fedupwithwin said:**
> Uh, excuse me....  Many people have been having problems getting perfectly good USB drives to mount properly.  If you want proof of this statement, please do a forum search using the keywords "memory stick", "pen drive" or "USB memory".

I can't verify the validity of this comment, but I'm sure this wasn't the case with Grim's USB drive. It was more than just a problem formatting the drive in Dapper. Grim and I tried it in Windows NT, XP, and Vista machines earlier today and had no luck formatting it.

Interestingly enough, I had similar problems with a 256MB SD card a couple weeks ago. I mounted it in Dapper, moved some files to it, and when I tried accessing them later everything was gone. After that, I was unable to properly format it in WinXP, WinNT, Unbuntu and my Dell Axim Pocket PC. I wonder if Dapper could have, somehow, messed up our removable media?

---

### Post by fedupwithwin on 2006-10-11
I have'nt seen anything that would lead me to believe that my pen drive is bad.  I plug it in to my Ubuntu machine and it doesn't mount - I plug it into an XP machine and it mounts fine.  I believe this has something to do with the USB host controller chip on my Ubuntu machine.  I'm still researching this in my spare time.  So I'll post more as things come to light.

---

### Post by iceolate on 2007-07-31
Hey thanks, finally! I have a JetFlash that will show that there's still some space being used even though I deleted everything off it. I kinda wish there was a "right click>format" option in Nautilus. I would have to run over to my gf's Windows machine to format it. No more!
Thanks again.

---

### Post by fragos on 2007-08-16
I have a number of flash memory devices including SD, Memory stick and USB pen drives.  All work flawlessly with the manufactirer's formating.  I have one SD that won't function in a Palm E2 but works perfectly in my Canon camera and when plugged into the PC's card reader.  In the case of a memory card you might try reformating in a device that uses it, like your camera.

---

