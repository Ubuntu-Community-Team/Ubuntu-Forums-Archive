---
title: "How2:\\ Backup your Windows files with Live CD //"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-12-02
I tried to simulate the whole process that you will probably go through from the point where you booted up the Ubuntu Screen.
Note that I'm using **Dapper Draker 6.06 Live CD**

**1.)** Bootup your computer with the Ubuntu Live CD.
**2.)** Select **Start Ubuntu in Safe mode Graphics**!
**3.)_** Applications > Accessories > **Terminal**_

Type in Terminal:
**4.)** sudo fdisk -[COLOR="Red"]l[/COLOR]
> -l is small letter "[COLOR="Red"]**L**[/COLOR]" 
**5.)** Look at column _Boot_ and locate where the ***** is.
**6.)** Look at column _Device_ and locate which device it is next to *.  For instance it might look like this: **/dev/hda1**
**7.)** Look at column _System_ what does your * designated device say?
HPFS/**NTFS** or VFAT something with **FAT** will do fine!

If **FAT** then goto FAT section... 
If **NTFS** goto NTFS section...
> 
##[COLOR="Red"] hda1[/COLOR] might not be your designated device, you put whatever ID you got on **step 6**
## the character between ...utf8.. and ..umask... is a [COLOR="Red"]comma[/COLOR] "[COLOR="Red"],[/COLOR]" not a period character!

**[COLOR="DarkOrange"]----------------FAT----------------[/COLOR]**
**8.)** sudo mkdir /media/windows
**9.)** sudo mount /dev/[COLOR="Red"]hda1[/COLOR] /media/windows/ -t vfat -o iocharset=utf8[COLOR="Red"],[/COLOR]umask=000

**[COLOR="DarkOrange"]----------------NTFS----------------[/COLOR]**
**8.)** sudo mkdir /media/windows
**9.)** sudo mount /dev/[COLOR="Red"]hda1[/COLOR] /media/windows/ -t ntfs -o nls=utf8[COLOR="Red"],[/COLOR]umask=0222

**10.)** Go up to menu and click _Places > **Computer**_

Can you find your mounted Windows disk?  If not then you must have miss typed during step 9.  You might have gotten a message saying "unable to mount or access denied".  Then you will have to unmount the disk even though it didn't got mounted right!

**11.)** sudo umount /media/windows/
**12.)** Try step 9 again and make sure you're using the right section.  It's either **FAT** or **NTFS**.  Then make sure you typed the long complicated commands in **step 9** correctly.

---

