---
title: "Installing ubuntu on my laptop - Any suggestions welcome!"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by alter_ego on 2006-01-27
Hi All,
       n00b here. Been hearing great things about ubuntu, tried the live CD, loved it. Looking to install the real thing now. But that where i have a problem. I have a IBM thinkpad centrino notebook (R51), which has Windoze XP pro preinstalled on the 40 GB drive partioned as a single drive, i also have a 200 GB USB HDD at my disposal.
        So where do i install Ubuntu? Should i create 40 GB partition on the 200 GB HDD for Ubuntu and boot it from USB or should i re-format and parition my laptop HDD to 20GB each and install ubuntu and windoze XP. 
1) I am little reluctant to format the Laptop HDD, if i can avoid that, it will be great.
2) Is there a way to create a parition without loosing any data.
3) Will my PC performance be bad if i install on my USB drive and work from there?

Thanks in advance.

---

### Post by mcduck on 2006-01-27
Ubuntu's installer can shrink your winXP partition to make room for Ubuntu.

Before you install Ubuntu start windows in safe mode and run defrag to get all windows stuff neatly in the beginning of the disk.

After that there should be no problems, when installing you'll get an option to 'Resize IDE1 master, partition #1 (hda1) and use freed space'.

Here's a nice guide with pictures that might help you with dualbooting: [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")

edit: about the USB drive: I remember seeing here somewhere a threa about succesfully installing Ubuntu to USB disk, but generally that won't work easily so you'd beter to make at least system and swap partitions to the laptops HDD. If you want, you can create a /home partiton to the USB disk. I'd keep even that on the internal HDD so that the machine is usable even without the USB disk. You can mount it anyway to use it as a storage drive :)

---

### Post by Bartender on 2006-01-27
Hi, alter -
mcduck pointed you to the guide that I used to create a dual-boot W2K/Ubuntu just a coupla days ago.  It worked great, and I'd never done anything like this before.  I must add that the W2K install was fresh so there were no worries about losing data....  If you can, set your notebook up next to another computer w/ an internet connection; that way you can have the guide displayed on the connected machine and just walk thru the steps on your notebook.  W2K is NTFS on mine, so I followed the guide to make a FAT32 partition.  Don't know how to use that yet but I understand the reasoning behind creating it.  You end up with NTFS, FAT32, and the Linux file systems (ext3 and something else?) all on the same drive.  I didn't know you could do such a thing!

---

### Post by alter_ego on 2006-01-31
Thanks for your inputs guys. But one another quick question? Is a 40 GB drive enough for a dual boot machine. I kinda have a lot of apps on Windoze. That was a reason i was looking at using my USB drive. Any suggestions on that?

---

### Post by byen on 2006-01-31
Yes, it should be more than enough. For Instance..I dual boot my 30gb hard disc with XP and this is what I did...
WindowXP- 15gb
FAT32 -(as a common storage drive) -7gb
Ubuntu (ext3)- 8gb

And trust me I have installed a ton of apps and still have over 60% space left.. so go ahead and take the plunge...Goodluck and welcome to Ubuntu!

---

### Post by alter_ego on 2006-01-31
Gee, thanks. Will take the plung this weekend.

---

### Post by jimrz on 2006-01-31
Hi,

  Take a look  [**[COLOR="Sienna"]_[U][B][U]here_**[/U][/U][/COLOR][/B]]("http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#intro") for a highly recommended guide to installing ubuntu on a thinkpad, which is a little bit different than on a desktop especially considering that you do NOT want to mess up the Rescue and Recovery hidden partition. This one does not address dual boot, for that look [**_[COLOR="Sienna"]here[/COLOR]_**]("http://www.jkraemer.net/pages/t42_ubuntu"),  but it does talk about install on 2nd drive in the ultra bay, which should be similar to your external idea without the added issue of dealing with usb (search these forums for this and you will find plenty of info).

   I recently upgraded to T42 from my old 600x (which was not really suitable for a dual boot with all the data i already had on the 12Gb drive). Would think info for your R51 would not be that different, but search these formums for "R51" and  see if there are any quirks to be found.

   Also, is your LT formatted ntfs or FAT32? Both of mine were and still are FAT32, which makes it nice as you can mount in ubuntu and be able to both read and write your win partition from ubuntu.

  PS: I have not yet installed to my new LT (will either this weekend or the following, so here's to good luck to each of us.

---

