---
title: "Partition Problem"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Contrid on 2006-08-11
Hey Guys,

I'm having some minor problems with partitioning, so I can't install Ubuntu. I've managed to take a screenshot and upload that.

The problem is that I'm not sure if there is any activity. I've been waiting a while, but nothing seems to happen. Please have a look at the image below.

[IMG]http://www.tribulant.com/IMG/partition.png[/IMG]

Could anyone please give me some advice, cause I would really like to get this installed.

All the best,
Contrid.

---

### Post by coffeecat on 2006-08-11
I presume hda1 is your ntfs Windows partition. It seems you are trying to reduce it from 41GB to 10.5 GB, although 10.5 is not 29% of 41.1 - not according to my calculator. :wink: Is there another partition?

Questions. How much space is Windows using? Is it less than 10.5 GB? How much less? Have you checked this in Windows? Also, did you defragment your Windows partition before trying to reduce the partition size? There might be files spread all over the partition and the Linux installer won't be able to reduce its size.

---

### Post by Contrid on 2006-08-11
> **coffeecat said:**
> I presume hda1 is your ntfs Windows partition. It seems you are trying to reduce it from 41GB to 10.5 GB, although 10.5 is not 29% of 41.1 - not according to my calculator. :wink: Is there another partition?

Questions. How much space is Windows using? Is it less than 10.5 GB? How much less? Have you checked this in Windows? Also, did you defragment your Windows partition before trying to reduce the partition size? There might be files spread all over the partition and the Linux installer won't be able to reduce its size.

Thanks. I think that your comment is pretty helpful.
Should I defrag this drive in Windows? Or is there a way to do it in Linux?
I tried to resize the drive in Windows using PartitionMagic, but everytime it reboots, the computer freezes...so obviously it doesn't want to resize...probably due to the issue you spoke about.

Maybe I should just wipe the drive clean and install Linux on it. I have another backup drive to which I copied all my data...and all that is remaining on this Windows drive is basically Windows and all it's installed applications.

Tell me...
Will I be able to access my data on the NTFS backup hard drive? When I try it now, it gives me some sort of mount error. I'm running the live CD, so I'm not sure if that's the problem.

All help is greatly appreciated. Thanks alot!

---

### Post by coffeecat on 2006-08-11
> **Contrid said:**
> Should I defrag this drive in Windows? Or is there a way to do it in Linux?

I don't know of a way of doing it in Linux so, yes, defrag in Windows. I've not experienced this issue myself but I've read that a Windows swap file can get stuck at the end of the partition where it prevents the partition from being resized. Apparently the answer is to inactivate the swap file (don't know how to do that), defrag and then reactivate the swap file. (Point of information - Windows uses a swap file, Linux a separate swap partition.) I believe there are better third-party defragging Windows apps out there - better than the Windows one that is - but I don't know the details.

> **Contrid said:**
> Maybe I should just wipe the drive clean and install Linux on it. I have another backup drive to which I copied all my data...and all that is remaining on this Windows drive is basically Windows and all it's installed applications.


Are you sure you want to ditch Windows just yet? There's no shame in keeping Windows going if you want. :wink: I'd suggest at least making a disk image/ghost with something like Norton Ghost or Acronis (I can recommend Acronis) in case you want/need to go back to Windows.

> **Contrid said:**
> Will I be able to access my data on the NTFS backup hard drive? When I try it now, it gives me some sort of mount error. I'm running the live CD, so I'm not sure if that's the problem.

You don't say whether the backup drive is a removable usb device or an internal slave one. There is a simple mount command to mount ntfs partitions/devices, or you can put a line in /etc/fstab so that it is automounted on bootup once you have a working Linux installation on the hard drive. I don't know about ntfs and usb drives - I've never tried it. The easiest solution is to format an external drive as fat32. Then it can be read and written to by Windows and Linux. Linux can read ntfs but writing to ntfs is not recommended - it's still in development. Most if not all external usb devices are sold already formatted as fat32.

Post back with the details of your backup drive and I might be able to say something more definite.

---

### Post by Contrid on 2006-08-11
The backup drive is just another hard drive which is currently running as slave. It is an NTFS file system.

I don't mind wiping Windows, but right now it might be better to keep it, especially since I'm unsure about the data on the backup NTFS drive. If I have 100% insurance that I will be able to use that data, then I might just wipe the Windows installation.

If I do decide to drop everything on the Windows hard drive, can I just run the Ubuntu install from the live cd and select 'Erase All' ? Will everything work out fine then?

Man...I really appreciate your help. I actually know quite a bit about computers and stuff, but Linux is a jungle to me.

---

### Post by Contrid on 2006-08-11
I can always reinstall Window anytime, and there isn't really any data which I wish to keep, since I copied all my important things to the backup drive. So if I can access that, then I'm all set.

I was thinking of buying another drive today...specifically for Linux, but I have work to do, and thought that I might test Linux while I do the work. (some php coding)

What do you think? :)

Edit...
I'm defragging in Windows now...but it takes ages, and it's not fun. What guarantee do I have that defragging my drive will solve this problem of resizing?

---

### Post by saracen on 2006-08-11
Defragging has really nothing to do with the issue.  When you selected the resize, did you tell it to go ahead and apply the resize?  Your screenshot doesn't show the rest of the window so i can't tell.  It shouldn't have a problem resizing the ntfs partition.  Erasing it and installing on the whole drive will definitely work as well (since u're not afraid of losing the windows install).

As to your backup drive, it will work without a problem in Ubuntu.  By default it will have read-only permissions.  You will have to do a bit of tinkering to get read/write permissions on ntfs (search the forums for ntfs-3g for more info on that).

I know what you mean about defragging... it's a real pain.  Think about it this way: once u move to linux u'll never have to defrag again!  ;)

---

### Post by Contrid on 2006-08-11
> **saracen said:**
> Defragging has really nothing to do with the issue.  When you selected the resize, did you tell it to go ahead and apply the resize?  Your screenshot doesn't show the rest of the window so i can't tell.  It shouldn't have a problem resizing the ntfs partition.  Erasing it and installing on the whole drive will definitely work as well (since u're not afraid of losing the windows install).

As to your backup drive, it will work without a problem in Ubuntu.  By default it will have read-only permissions.  You will have to do a bit of tinkering to get read/write permissions on ntfs (search the forums for ntfs-3g for more info on that).

I know what you mean about defragging... it's a real pain.  Think about it this way: once u move to linux u'll never have to defrag again!  ;)

Damn...I don't know what Windows did to this drive. I can't even resize it in Windows itself using Partition magic. I know the drive is not damaged or anything...so it might just be the defrag problem.

As for accessing the NTFS internal drive, I basically just need to retrieve data and copy it to my Linux ext3 partition for use. I don't need to write back to the NTFS drive...so that's not a problem.

Defragging is now on 4%...and I seriously don't want to wait. lol...what did Bill think? :) Tell me...when I choose the 'Erase...blah...blah' to install Linux on the Windows drive, will it format the drive? I hope it does, since then everything will be clean. If it won't format automatically, then I might need to do that in command prompt before booting from the Linux CD.

Thanks again for your help guys. I'm really getting somewhere here. Just another post or two, and I'll have it all figured.

Off topic :
Terminal commands. Can I open a terminal window from anywhere in Ubuntu and type a command and it will execute the same from any location?

---

### Post by RRS on 2006-08-11
After windows finishes defragging reboot the live cd. 

Use the gparted utility from the live cd to resize windows and create new partitions for Ubuntu. Besides an ext3 for the system you'll also want a small (app. one and a half to twice your ram) swap partition.

Most people also create a fat32 partition to share data between Ubuntu and windows.

When you install select the third, "manually edit" option and simply assign the mount points to your partitions. 

[Here's]("http://www.psychocats.net/ubuntu/installing.html") a good guide to installing from the live cd.

Aysiu also has a lot of good info on the other pages of his site.

---

### Post by Contrid on 2006-08-11
Thanks for that link. I've been reading those articles today, and they are awesome. Excellent resources for a newbie like me...and anyone else really.

I am now thinking of using Partition Magic to convert my NTFS backup drive to FAT32 as 'coffeecat' said that Linux can read and write from and to a FAT32 drive. Though I've read that Partition Magic isn't always as reliable as it should be, and I might just lose my data. I'll keep on thinking about that...unless it's not too difficult to mount my NTFS drive.

I'll finish up the defrag and do as you suggested. Thanks for the help. Any other comments are greatly appreciated. Thank you.

---

### Post by Contrid on 2006-08-11
Even though I defragged my hard drive, it still didn't make a difference, so I just dumped the XP installation and installed Ubuntu.

I'm really impressed with this OS, and hope to see some more amazing things in the near future.

I am also very satisfied with the fact that most of the features on my Logitech MX 5000 desktop set work great. (I like that volume bar) :)

---

### Post by xpod on 2006-08-11
Theres a couple of good defrag.exe`s out there for windows.

I use(USED too)one simply called "scan/defrag" that shuts down any of those running processes that can slow down the defrag(or even stop it)

It defrags in about a quarter of the time.....NOT that you`ll NEED it now eh....:D

---

### Post by imhdd on 2006-08-11
Contrid, you won't regret moving to Ubuntu. I started with it in Feb of this year. Been building and repairing Win computers for about eleven years and the change to Linux has been hard but it's worth it. I tried other distros before Ubuntu and was totally lost ... then in Feb got Ubuntu installed and struggled for a while and now I'm proud to do all my main computing on Ubuntu. I still have Win98SE dual booting on two computers for an HTML editing program but don't use Win for anything else. All my surfing and  banking are done with Ubuntu. Just keep reading and experimenting. You'll be proud of your accomplishments and fortunate to stop donating to Mr Gates favorite charities. Good luck.

By the way, I'm 74 and my wife who also loves Ubuntu is 69 (she plays on-line poker using Wine. If we old folks can do it, I know you can.
IMHDD

---

### Post by Contrid on 2006-08-11
> **imhdd said:**
> Contrid, you won't regret moving to Ubuntu. I started with it in Feb of this year. Been building and repairing Win computers for about eleven years and the change to Linux has been hard but it's worth it. I tried other distros before Ubuntu and was totally lost ... then in Feb got Ubuntu installed and struggled for a while and now I'm proud to do all my main computing on Ubuntu. I still have Win98SE dual booting on two computers for an HTML editing program but don't use Win for anything else. All my surfing and  banking are done with Ubuntu. Just keep reading and experimenting. You'll be proud of your accomplishments and fortunate to stop donating to Mr Gates favorite charities. Good luck.

By the way, I'm 74 and my wife who also loves Ubuntu is 69 (she plays on-line poker using Wine. If we old folks can do it, I know you can.
IMHDD

Thanks for the motivation!
I've been fiddling with Linux (ubuntu) all day long, and I am already proud to say that I've managed to accomplish many great things...for me that is. :)

I've mounted my Windows NTFS hard drive, and currently I'm working on a client's website using 'Screem' with music in my ears.

The experience is awesome, and I think that this is much faster than Windows...best of all...it hasn't crashed once since the installation. ;)

---

