---
title: "Brand-spanking new to Ubuntu"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Grimesville89 on 2006-10-27
[FONT="Arial"][SIZE="3"]I decided to give Ubuntu a try after hearing Leo Laporte discuss it on his KFI talk show.  I am currently using Windows XP and just ordered the Ubuntu CD, so I am waiting patiently for it to show up in the mail.  

My question is, most of my programs that I currently use are compatible,except one that I can not live without.  It is my daughters homeschool curriculum that is not compatible with anything but Windows. I am assuming that I would need to partition my 80G HD into 2 different partitions, currently it has only one, one for Ubuntu and one for XP.  Is there a way that I can partition my HD without having to reformat and reinstall XP?  How large do I need to make the partitions?

--GV89
[/FONT][/SIZE]

---

### Post by JayTee on 2006-10-27
When you install Ubuntu you can resize your XP partition dynamically and then install Ubuntu on the free space you've created. There are several caveats to this.
#1:
Before you install Ubuntu do the following.
from the command line in Windows type the following.
chkdsk C: /F
it will tell you it cannot perform the check while the volume is mounted. It will ask you if you want to run this the next time the computer is rebooted. Answer yes to this and then restart your computer. chkdsk will run on startup. If your hard disk is in good shape it should run through it and correct any minor errors and will report any serious errors. If you get lots of errors I'd hold off on installing Ubuntu.
#2: From the Start Menu go to Accessories/System Tools and run Disk Defragmenter. Click on the Analyze button (you have to do this to defrag) and once the disk has been analyzed click on Defragment. This will take awhile to finish. 
#3: There are several good how-to's in the How-To's section of this site that deal with dual booting Windows and Ubuntu. I'd read a few so you know what to expect before you start. I'd also do searches for your hardware components, especially your graphics card, sound card and ethernet card to make sure there aren't any incompatibilities. Although I've never had a problem on either of the two machines I've installed Dapper on at home with hardware recognition or operation others have. Mostly with older hardware or uncommon hardware. One common thread is if you have a Broadcom network chipset and if you do you're most likely gonna run into trouble. Once you've read enough here to feel comfortable installing Ubuntu on your particular hardware boot with the Ubuntu LiveCD and play around with it before you install. The LiveCD should allow you to test drive the OS with network functionality and everything else working. At least on most computers it does. If it won't boot properly you may need to use the Alternate CD. If the LiveCD does boot and you decide after using Ubuntu for a bit that do want to install just click on the Install icon on the desktop. When you get to the partition portion of the install you can resize your Windows partition and leave the rest of the space blank. Once you resize and have committed the change you need to hit the back button and choose the option to Use Available space. This will create the root partition and swap partition for you. After you just go through the rest of the install and usually take the defaults. It will ask for questions to setup your user account/password and an administrative password. I recommend you don't use the same password for both. I'd also write down the screen resolution settings of your Windows configuration i.e. 1024x768 and the refresh rate, i.e. 60hz, 72hz, 85hz before the install so when you get to the video configuration portion you know what to answer. If for some reason things go wrong and you can't complete the install and neither Windows or Ubuntu will boot then boot from your Windows CD and choose Recovery from the first menu. Choose the Windows partition (Usually 1.) and at the command prompt type FIXMBR and then exit and remove the CD before the computer restarts. Good luck and enjoy Ubuntu!

---

### Post by DJ Scribblinni on 2006-10-27
If you want to save your windows partition, an easy way is to defrag that hard drive.  Then using the Live Ubuntu CD, there is a program called QTparted that will run on the Live CD that will allow you to actually shrink the Windows partition by cutting off the empty space and using it for other patition possibilities.  Don't try to make it smaller than the amount of info that is being used.  You shouldn't loose your data, I've never had problems with it.  
After the partitioner has divided the windows partition, you'll be able to create partitions, I would recomend 5 or 6GB for a normal use for Ubuntu, about 1GB pending the memory on your computer for a swap partition, and if you have even more space left, why not use that as a FAT32 partition, where you can save files to, in which both windows and linux will be easily abled to modify the files in between bootups.  
After the partitioning, go ahead and install Ubuntu and have some fun with it. Best of Luck

Here's a guide that you can follow, it's pretty simple, though they start off with a fresh install of windows.  

[http://www.hezardastan.org/breezy_xp_dualboot/en/]("http://www.hezardastan.org/breezy_xp_dualboot/en/")

---

### Post by ReaderRat on 2006-10-27
You can dual-boot Win & Ubu.
[**Dual-Booting (One HDD)**](http://users.bigpond.net.au/hermanzone/)
If you plan to share files, you will need a FAT partition or an ext2 partition. Please look into this before you make up your mind - multiple posts here about it - go to "Tags" at the top of the page and search on some keywords (FAT32, ext2, etc.
[**Partitioning (XP & Ubuntu)**](http://psychocats.net/ubuntu/partitioning)
Also
gparted Live CD site
     [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/download.php)

---

