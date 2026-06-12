---
title: "Help with SATA to USB drive?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by robio376 on 2006-07-20
Here's my problem. I had 2 250GB SATA drives in my WMC2005 box and only an 120GB IDE drive in my Ubuntu box. I want to remove the second 250GB SATA from my Windows Box and place it in the SATA to USB 2.0 external enclosure that I purchased. All my media files such as mp3's, videos, and so on are stored on this drive I removed. I installed the hardisk in the enclosure an plugged it into my Ubuntu's usb port. Ubuntu mounted it and no probs...But I do not have write access to it. Instead of playing around with that new NTFS read write for Linux, I burned all the media to DVD after plugging it back into my XP box. Well after about 55 DVD's I have a complete backup..(Don't backup 250gigs if you have a life.. took me about a week. And yes I know what dual layer DVD's are!) Windows would only format the external drive to NTFS. I don't want NTFS or Windows for that matter. Well I formatted it any way to get rid of anything. Replugged it into my Ubuntu box and the drive was recognized as NTFS with no write permissions. I apt installed gparted and tried to format to Ext3 filesytem..no such luck. Drive shows as unrecognized. Basically all I want to do is have this external drive connected to my Ubuntu server with an Ext3 filesystem so my Ubuntu Laptop and Ubuntu Desktop, my daughter's Edubuntu desktop, any my wife's Kubuntu laptop, and my Mythtv box connected to our tv can have read and write access to it. Currently I have only one Windows box(WMC2005)in which the drive WAS connected to. I plan to dual boot the WMC2005 box with Ubuntu but wish keep on Windows box for some games. I know this is a long post but I try to explain in detail.

---

### Post by catlett on 2006-07-20
I don't know why the drive isn't recognised. You can try 2 things.
1. put the drive in the windows box and format it to fat32. Set it up to ubuntu again and see if gparted recognises it. Format to ext3. (you could keep it fat32 because linux reads and writes to it fine buit it has a 4gb file size limit that may conflict with your dvds if some are over 4gb)
2. Download the gparted live cd. I have had great success with it. It recognises my ntfs windows drive and my external usb drive (that use to be ntfs but gparted made it fat32)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) This is the link. The iso is small 30mb. The best part is it is a live cd so it can make changes to the disk because it is unmounted already.

---

### Post by robio376 on 2006-07-20
Actually I have booted Knoppix and running qtparted to try to format the drive. But it has been 2 days and sitting at 19%. I will try your option. Thanks for the reply!

---

### Post by robio376 on 2006-07-20
qtparted seems to still be working. I will let it run till it completes. Hopefully that does it. I also found out that SATA to USB drive enclosures are fairly new and maybe that might be the problem (Hopefully not!) Well only time will tell. Thanks

---

### Post by robio376 on 2006-07-20
Would it be better to format this drive to a Fat32 so all my buddies that use Windows can have read and write access? Sometimes my friend connect to my network to game and share files but I haven't converted them to Ubuntu (YET!) So would fat32 be a better option?

---

### Post by robio376 on 2006-07-20
> **robio376 said:**
> Would it be better to format this drive to a Fat32 so all my buddies that use Windows can have read and write access? Sometimes my friend connect to my network to game and share files but I haven't converted them to Ubuntu (YET!) So would fat32 be a better option?
But I wan't read and write access from all OS's! Thanks!

---

### Post by catlett on 2006-07-20
It may be the sata to usb. I hope not. Just for the sake of full disclosure, my enclosure is IDE to USB2 and ubuntu has been having sata install issues. Hopefully it won't have sata enclosure issues.
Good luck

---

### Post by robio376 on 2006-07-20
This is the drive enclosure [http://www.newegg.com/Product/Product.asp?Item=N82E16817121185]("http://www.newegg.com/Product/Product.asp?Item=N82E16817121185") with a IBM 250GB 16mb cache drive. When I purchased this enclosure it was the only enclosure that supported Sata to USB. So maybe I need wait for better support or come up with a solution that will benefit everybody. Thanks!

---

### Post by robio376 on 2006-07-20
> **catlett said:**
> It may be the sata to usb. I hope not. Just for the sake of full disclosure, my enclosure is IDE to USB2 and ubuntu has been having sata install issues. Hopefully it won't have sata enclosure issues.
Good luck
Well Ubuntu recognized the drive an mounted it with no problems. But my other ubuntu machines didn't have write access to it. And I want to be able to save files on this drive from all my Ubuntu machines with no problems...Hence I want to convert it to a Linux format so I can set permissions.

---

### Post by catlett on 2006-07-20
Since you posted yours, I'll post mine :-D  [http://www.mdmm.com/products/enclosures/35aluminumcombo.asp](http://www.mdmm.com/products/enclosures/35aluminumcombo.asp) I have no issues. Ubuntu always recognises it no matter how I have it hooked up. Whether it is connected by USB2 or Firewire or whether it is on at startup or I power up after I log in. Hopefully you'll have the same results.

---

### Post by robio376 on 2006-07-20
> **catlett said:**
> Since you posted yours, I'll post mine :-D  [http://www.mdmm.com/products/enclosures/35aluminumcombo.asp](http://www.mdmm.com/products/enclosures/35aluminumcombo.asp) I have no issues. Ubuntu always recognises it no matter how I have it hooked up. Whether it is connected by USB2 or Firewire or whether it is on at startup or I power up after I log in. Hopefully you'll have the same results. Thanks but Ubuntu has no problems with IDE to USB enclosures. I have 2 laptop drive enclosures that have been no problem to convert to a ext3 filesytem. Only the SATA to USB enclosure is giving problems. What is your take on just making the SATA enclosure to a FAT32? Would this be a better option? I do have partion magic.. but don't know if it will work with a SATA to USB enclosure. What are your thoughts?

---

### Post by robio376 on 2006-07-20
> **catlett said:**
> I don't know why the drive isn't recognised. You can try 2 things.
1. put the drive in the windows box and format it to fat32. Set it up to ubuntu again and see if gparted recognises it. Format to ext3. (you could keep it fat32 because linux reads and writes to it fine buit it has a 4gb file size limit that may conflict with your dvds if some are over 4gb)
2. Download the gparted live cd. I have had great success with it. It recognises my ntfs windows drive and my external usb drive (that use to be ntfs but gparted made it fat32)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) This is the link. The iso is small 30mb. The best part is it is a live cd so it can make changes to the disk because it is unmounted already. Windows does not give the option to format to Fat32! Only NTFS.

---

### Post by catlett on 2006-07-20
Really? Did you go to My Computer and right-click to get on option menu. It didn't have a format option. And it didn't have a fat32 option?
Wow I'm surprised. 
Try going to Start<Control Panel<Performance and Maintenance<Administrative Tasks<Computer Management<Storage<Disk Management
When I go there and select a partition and then right-click, I get a menu. One option is "format". When I select that, a menu appears in another window. It has a line for the volume name and then a line for file system. NTFS is the default but if I hit the drop down arrow, fat32 is given as a choice.I have XP PRO service pack 2 if that means anything. I don't think it should but just to state it all.

---

### Post by robio376 on 2006-07-22
> **catlett said:**
> Really? Did you go to My Computer and right-click to get on option menu. It didn't have a format option. And it didn't have a fat32 option?
Wow I'm surprised. 
Try going to Start<Control Panel<Performance and Maintenance<Administrative Tasks<Computer Management<Storage<Disk Management
When I go there and select a partition and then right-click, I get a menu. One option is "format". When I select that, a menu appears in another window. It has a line for the volume name and then a line for file system. NTFS is the default but if I hit the drop down arrow, fat32 is given as a choice.I have XP PRO service pack 2 if that means anything. I don't think it should but just to state it all.
Yes I tried both of your ideas under my Windows box. But it will not let me format it to fat 32. So I found my old partition magic disk and used that as gparted would never complete the format. Partition Magic done the trick and I was able to format it to an ext3 filesystem. Thanks for all your help 
!

---

### Post by catlett on 2006-07-22
Great. I use Partition Magic but have lately been using gparted live. I don't always mention it because you need to purchase it. I have had my copy for a couple of years and it never gave me an error or corrupted anything. It even converted my XP install into ntfs without losing data (I used a backup to reinstall XP but I didn't realise the partition was fat32. anyways the backup didn't convert the partition and it installed xp to fat32. PM converted it to ntfs without loosing any data) 
Well, glad it worked, even though I didn't ive you the correct way to do it,

---

