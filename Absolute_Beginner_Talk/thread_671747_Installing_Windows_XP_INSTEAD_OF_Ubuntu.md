---
title: "Installing Windows XP INSTEAD OF Ubuntu"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Dylan H on 2008-01-18
Hello all, I recently installed Ubuntu on my Acer Aspire 5315 laptop. I think it's a great OS, but I really want to install Windows XP **_instead of_** Ubuntu. I have tried installing Wine, but no avail. Any help is greatly appreciated!

Dylan H

---

### Post by CCNA_student on 2008-01-18
Just to be sure, do you want both Ubuntu and Windows or just Windows.

---

### Post by wolfen69 on 2008-01-18
we cant help you here. go away. just kidding. just boot to your xp restore cd or restore partition. ubuntu will magically go away.

---

### Post by Dylan H on 2008-01-18
I just want Windows XP, and there is no XP restore disc or restore partition. I had vista before, and I now want XP. Thanks for replying! (:

---

### Post by gn2 on 2008-01-18
Here you go: [http://www.amazon.com/Microsoft-Windows-System-Builders-Version/dp/B000JTFVME/ref=pd_bbs_1?ie=UTF8&s=software&qid=1200711925&sr=8-1](http://www.amazon.com/Microsoft-Windows-System-Builders-Version/dp/B000JTFVME/ref=pd_bbs_1?ie=UTF8&s=software&qid=1200711925&sr=8-1)

---

### Post by iansane on 2008-01-18
If you want an alternative to WINE , don't want to dual boot, and want to keep ubuntu, you could use vmware and install windows on a virtual machine inside of ubuntu. It feels just like your on your old windows system except for a few issues with usb and shareing folders with the host os (ubuntu).
vmware server I think is required to create the vm machine but the vmware player found in ubuntu's add/remove programs will play them. I'm not sure, I just use the vmware server to make and play them. There's a new version about to be released that should fix the usb conection problem

---

### Post by stevescripts on 2008-01-18
You may want to re-think your plan, when you find out how much
a WinXP OS costs ! ....

Steve

---

### Post by thelatinist on 2008-01-18
> **Dylan H said:**
> I just want Windows XP, and there is no XP restore disc or restore partition. I had vista before, and I now want XP. Thanks for replying! (:

Yeah, you'll have to drop about $200 on an XP install CD.

---

### Post by Methuselah on 2008-01-18
If he had vista before I think he may be able to get a 'downgrade' using the valid vista license.

---

### Post by thelatinist on 2008-01-18
> **Methuselah said:**
> If he had vista before I think he may be able to get a 'downgrade' using the valid vista license.

I did not know this.  According to [this]("http://download.microsoft.com/download/d/2/3/d23b9533-169d-4996-b198-7b9d3fe15611/downgrade_chart.doc") document on the Microsoft website, Vista Business and Vista Ultimate can be downgraded to XP Pro if he has a valid Vista CoA; Vista Home and Vista Home Basic cannot be downgraded.  Also, he will still need a valid XP install disc to perform the downgrade.

---

### Post by JoshuaRL on 2008-01-18
Hehehe.  I bet Redmond was happy that he was leaving Linux.  That is until he said he wanted to downgrade to XP.  Hehehe.

---

### Post by Dylan H on 2008-01-18
I already have an install disc.

---

### Post by Dylan H on 2008-01-18
I completely erased Windows Vista when I installed Ubuntu. I have an XP disc just laying around, and I'd like to use that. There are no 'backup' discs. The XP install disc's setup is a .exe file, can I use wine to install XP?

---

### Post by seventhc on 2008-01-18
Just put the disk in the CD tray, make sure your computer is set to boot from cd, reboot and it should go into the xp install. Make sure you have the key that goes with the cd.
You don't need wine if to install xp. :)

---

### Post by thelatinist on 2008-01-18
> **Dylan H said:**
> I completely erased Windows Vista when I installed Ubuntu. I have an XP disc just laying around, and I'd like to use that. There are no 'backup' discs. The XP install disc's setup is a .exe file, can I use wine to install XP?

Your XP install CD may be bootable.  Just try booting to it the same way you booted to your Ubuntu LiveCD and run the installation program.  When it asks, just let it format your HD to NTFS and you'll be all set.

---

### Post by Dylan H on 2008-01-18
I've tried this before, there is a grey bar along the bottom of the screen that reads "Setup is loading files (whatever it's loading). Eventually it asks me if I want to install XP, I say yes. I get this error message :

"Setup did not find any hard disk drives installed in your computer.

Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct. This may involve running a manufacturer-supplied diagnostic or setup program.

Setup cannot continue. To quit Setup, press F3."

The hard disk works just fine in Ubuntu.

---

### Post by jleaker01z on 2008-01-18
> **Dylan H said:**
> I've tried this before, there is a grey bar along the bottom of the screen that reads "Setup is loading files (whatever it's loading). Eventually it asks me if I want to install XP, I say yes. I get this error message :

"Setup did not find any hard disk drives installed in your computer.

Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct. This may involve running a manufacturer-supplied diagnostic or setup program.

Setup cannot continue. To quit Setup, press F3."

The hard disk works just fine in Ubuntu.

You have a serial ATA hard drive.  You will have to put the drivers for it on a FLOPPY, yes I said a 20 year old obsolete FLOPPY, and when Windows setup asks you if you need to install a SCSI driver hit F6 and it will pull the driver off the floppy.

---

### Post by Dylan H on 2008-01-18
I uh... don't have a floppy drive on my laptop. Nor do I have an external one.

---

### Post by jleaker01z on 2008-01-18
> **Dylan H said:**
> I uh... don't have a floppy drive on my laptop. Nor do I have an external one.

Cant install windows without one then.  Isnt Windows grand? ;)  

I know it's stupid, but hey, cant expect much from a monopoly.

BTW...you can get the driver you need from the laptop manufacturer, or off the driver CD that came with your system.  But you will have to get a stupid floppy to make it work.  I havent used a floppy for anything other than a windows install in at least 10 years.  Why it has to be a floppy I never was able to figure out.  Now my external floppy is just collecting dust.  Wanna buy it? :D

---

### Post by thelatinist on 2008-01-18
> **Dylan H said:**
> I uh... don't have a floppy drive on my laptop. Nor do I have an external one.

Google is your friend (took 30 seconds): [http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

---

### Post by jleaker01z on 2008-01-18
> **thelatinist said:**
> Google is your friend (took 30 seconds): [http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

Cool...didnt know that.  Too bad I've sworn off Windows.  Well maybe not... ;)

---

### Post by thelatinist on 2008-01-18
> **jleaker01z said:**
> Cool...didnt know that.  Too bad I've sworn off Windows.  Well maybe not... ;)

Umm...haven't we all spent the last hour and a half trying to help you install Windows?

---

### Post by jleaker01z on 2008-01-18
How dare you insult me!  I havent used Winblowz in at least 8 months.  Ive been here trying to help people with Ubuntu.  :P

---

### Post by thelatinist on 2008-01-19
> **jleaker01z said:**
> How dare you insult me!  I havent used Winblowz in at least 8 months.  Ive been here trying to help people with Ubuntu.  :P

Sorry!  I thought I was replying to Dylan H.  Didn't mean to offend!

---

### Post by Dylan H on 2008-01-20
See here: [http://ubuntuforums.org/showthread.php?p=4173409](http://ubuntuforums.org/showthread.php?p=4173409)

---

### Post by mikerman55 on 2008-02-12
> **thelatinist said:**
> I did not know this.  According to [this]("http://download.microsoft.com/download/d/2/3/d23b9533-169d-4996-b198-7b9d3fe15611/downgrade_chart.doc") document on the Microsoft website, Vista Business and Vista Ultimate can be downgraded to XP Pro if he has a valid Vista CoA; Vista Home and Vista Home Basic cannot be downgraded.  Also, he will still need a valid XP install disc to perform the downgrade.

NOT hardly.
go to pricewatch.com and get a legal win xp pro disk for $84.00 or a xp pro 64 disk for 87.95. they are legal and they work. 

however they do NOT work once ubuntu has been installed. i was going to go from that horror vista to ubuntu and use xp as my backup. good plan. unfurtunatly ubuntu did not work with my wifi or give me any sound. when i tried to go with my "backup plan" no luck. windows would not install on the disk. it could not find the disk on my acer. ubuntu could with no problem but not any of the microsoft products i tried. (Vista, XP or XP64) so i am back to using ubuntu on a semi crippled laptop.

---

### Post by thelatinist on 2008-02-12
> **mikerman55 said:**
> NOT hardly.
go to pricewatch.com and get a legal win xp pro disk for $84.00 or a xp pro 64 disk for 87.95. they are legal and they work. 

We are talking about two different things.  You are talking about buying a new copy of XP with a valid XP CoA and serial number.  I was talking about downgrading from Vista to XP using a **Vista** CoA and serial number.


> however they do NOT work once ubuntu has been installed. i was going to go from that horror vista to ubuntu and use xp as my backup. good plan. unfurtunatly ubuntu did not work with my wifi or give me any sound. when i tried to go with my "backup plan" no luck. windows would not install on the disk. it could not find the disk on my acer. ubuntu could with no problem but not any of the microsoft products i tried. (Vista, XP or XP64) so i am back to using ubuntu on a semi crippled laptop.

It is simply not true that you cannot install Windows once you have installed Ubuntu.  I don't know what your problem is, as you offer no specifics, but is it possible you have a SCSI hard drive?  If so, the Windows install CD will not have a driver to recognize it and you will have to obtain one from your manufacturer.  Have you tried checking in BiOS to make sure your HD is being detected?

---

### Post by seventhc on 2008-02-12
You would probably first need to delete the existing partitions using gparted, (I don't think windows can recognize your drive since it isn't NTFS. Thats why it didn't install before)
Then boot from the windows cd and it will say*something like "Hey, theres no OS here, you want me to install myself on here???"* Then you can answer yes and your back to windows.
Not sure what cd you have, but you might need to put vista back on first.

Boot from the live cd then open a terminal and put:
```
 gksu gparted
```Then delete the partitions. :)

---

