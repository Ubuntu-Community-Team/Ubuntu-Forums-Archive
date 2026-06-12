---
title: "Boot issue--BIOS?(was: Totally clueless...please help.)"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by dizzylizard on 2006-09-18
I have a compaq presario 7594 with 256MB ram, a 60GB HDD and a CDRW drive...during Ubuntu install from Live CD, partitioning erased the BIOS partition...now I can't get into bios settings.  also, ubuntu still won't load from the HDD.....starts to, then either GRUB fails (error 18), or it starts and gets to "mounting root filesystem"..."Waiting for filesystem"...and then it freezes up...I am new to ubuntu, new to linux, and starting to wonder where I put my winblows CDs...

BTW, the Live CD still runs fine, although during boot, it says 
"hdd - no disk in drive" a bunch of times...
help?  I've looked through all the faq's and haven't been able to find this exact problem addressed...

---

### Post by bodhi.zazen on 2006-09-18
Start by restoring BIOS.

---

### Post by emarkay on 2006-09-18
There may not be a "BIOS partition" on your Compaq/HP unit.  I pulled this up via Google, so maybe you need to confirm where the BIOS is on your machine.

[http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1056850&admit=-682735245+1158631207384+28353475](http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1056850&admit=-682735245+1158631207384+28353475)

If the BIOS is damaged you may not be able to do anything with your PC.  You may need to clear the CMOS ROM by pulling the battery. I think that there may also be a FDISK partition problem - usually that's seperate from a BIOS problem, but I'd have to look at that machine's specs to confirm, however, not being able to to see the HDU does sound like a hardware problem at the BIOS level.  (It may be spinning in the drive, but not reading anything!)

Ubuntu gurus need to chime in on the error code, and if there are any known conflicts with this Compaq machine...

---

### Post by powder on 2006-09-18
[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

You may need to create a /boot partition at the beginning of your hard drive so that your BIOS can access the kernel.  This is common on old machines and the only other way around this is a BIOS update.

---

### Post by dmizer on 2006-09-18
first of all, you get into a situation like this ... don't panic and get crazy with trying solutions.  you can do real damage then.  slow down, take your time and make sure you know what you're doing before you take action.

also, you can be well assured that you're not the first to run into this problem in a linux or windows situation.

you should be able to get your bios partition from hp's site.

the site's not working right now for me.  i think they're down for maintenance.

but start here: [http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=us&taskId=135&prodClassId=-1&prodTypeId=12454&prodSeriesId=96412](http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=us&taskId=135&prodClassId=-1&prodTypeId=12454&prodSeriesId=96412)

---

### Post by dizzylizard on 2006-09-19
> **bodhi.zazen said:**
> Start by restoring BIOS.

OK...right now, the only use I have of this box is via ubuntu live CD...how do i go about restoring the bios?  Bear in mind that I have no floppy drive to install, and the cd won't let me save anything to the hdd...

been offgrid for a few years (since 2000) and trying to remember/catch up...:(

---

### Post by dizzylizard on 2006-09-19
> **dmizer said:**
> first of all, you get into a situation like this ... don't panic and get crazy with trying solutions.  you can do real damage then.  slow down, take your time and make sure you know what you're doing before you take action.

also, you can be well assured that you're not the first to run into this problem in a linux or windows situation.

you should be able to get your bios partition from hp's site.

the site's not working right now for me.  i think they're down for maintenance.

but start here: [http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=us&taskId=135&prodClassId=-1&prodTypeId=12454&prodSeriesId=96412](http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=us&taskId=135&prodClassId=-1&prodTypeId=12454&prodSeriesId=96412)


went there...they don't have anything for linux...just 
 	» 	Microsoft Windows 2000
	» 	Microsoft Windows 95
	» 	Microsoft Windows 98
	» 	Microsoft Windows ME
	» 	Microsoft Windows NT 4.0
	» 	Microsoft Windows XP
Plus, I can only run from the ubuntu live cd (which works great!) but it won't let me set the permissions on the hard disk to to save the executable file for restoring the bios...I do have a 60 meg flash card I can read and write to...If I could find a linux executable...

---

### Post by dizzylizard on 2006-09-19
> **emarkay said:**
> There may not be a "BIOS partition" on your Compaq/HP unit.  I pulled this up via Google, so maybe you need to confirm where the BIOS is on your machine.

[http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1056850&admit=-682735245+1158631207384+28353475](http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1056850&admit=-682735245+1158631207384+28353475)

If the BIOS is damaged you may not be able to do anything with your PC.  You may need to clear the CMOS ROM by pulling the battery. I think that there may also be a FDISK partition problem - usually that's seperate from a BIOS problem, but I'd have to look at that machine's specs to confirm, however, not being able to to see the HDU does sound like a hardware problem at the BIOS level.  (It may be spinning in the drive, but not reading anything!)

Ubuntu gurus need to chime in on the error code, and if there are any known conflicts with this Compaq machine...
I believe the post you're referring to at that site is: 
-----------------lifted post follows------------------- 
John Kirk  This member has accumulated 1500 or more points 	
Sep 3, 2006 15:16:13 GMT    Unassigned 	
Moon Light

The BIOS is not a hard drive partition it is stored in a chip on the motherboard and while it is possible to have a failure or to damage the BIOS by improperly "flashing" it, it would be very difficult to do so "inadvertantly".

If your computer starts up with the Compaq logo screen and/or POST information and has the F10 Setup message and you can get to the F10 Setup your BIOS is fine.

-----------Windows 2K and social niceties deleted-------------------------


I'm experiencing a different problem...I don't have the f10 option.  I press it, I hold it...before the compaq bootsplash, during, after...no bios settings...no f10 setup message...without the CD, it starts to access the hard drive, starts loading, then fails...with the CD, during hardware driver installation, after X configuration, it reads:
     [random numbers here] hda - no disk in drive
     [random numbers here] hda - no disk in drive
     [random numbers here] hda - no disk in drive
mount not executed.

One site I googled said to fix this by setting the bios to auto-detect the hard drive and extend the pre-check delay...but I can't get into the bios.

>>>You may need to clear the CMOS ROM by pulling the battery.<<<

I did that already...that's when I lost the f10 option to get into the bios...I did that to fix a 1782-disk controller failure- error message...fixed it, but lost the bios...:(

Is there a reputable site where I could get my bios flashed right?

---

### Post by Brunellus on 2006-09-19
The thread title of this post has been changed to better reflect the nature of the help request.

In the future, please use the thread title to give a description of the TYPE of problem you're having.  This lets users who know how to help you know that they can help you.

[It's all about matching questions to answers](http://www.ubuntuforums.org/showthread.php?t=260731)

---

### Post by dizzylizard on 2006-09-19
> **emarkay said:**
> There may not be a "BIOS partition" on your Compaq/HP unit.  I pulled this up via Google, so maybe you need to confirm where the BIOS is on your machine.

[http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1056850&admit=-682735245+1158631207384+28353475](http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1056850&admit=-682735245+1158631207384+28353475)

If the BIOS is damaged you may not be able to do anything with your PC.  You may need to clear the CMOS ROM by pulling the battery. I think that there may also be a FDISK partition problem - usually that's seperate from a BIOS problem, but I'd have to look at that machine's specs to confirm, however, not being able to to see the HDU does sound like a hardware problem at the BIOS level.  (It may be spinning in the drive, but not reading anything!)

Ubuntu gurus need to chime in on the error code, and if there are any known conflicts with this Compaq machine...
I believe the post you're referring to at that site is: 
-----------------lifted post follows------------------- 
John Kirk  This member has accumulated 1500 or more points 	
Sep 3, 2006 15:16:13 GMT    Unassigned 	
Moon Light

The BIOS is not a hard drive partition it is stored in a chip on the motherboard and while it is possible to have a failure or to damage the BIOS by improperly "flashing" it, it would be very difficult to do so "inadvertantly".

If your computer starts up with the Compaq logo screen and/or POST information and has the F10 Setup message and you can get to the F10 Setup your BIOS is fine.

-----------Windows 2K and social niceties deleted-------------------------
I'm experiencing a different problem...I don't have the f10 option.  I press it, I hold it...before the compaq bootsplash, during, after...no bios settings...no f10 setup message...without the CD, it starts to access the hard drive, starts loading, then fails...with the CD, during hardware driver installation, after X configuration, it reads:
     [random numbers here] hda - no disk in drive
     [random numbers here] hda - no disk in drive
     [random numbers here] hda - no disk in drive
mount not executed.

One site I googled said to fix this by setting the bios to auto-detect the hard drive and extend the pre-check delay...but I can't get into the bios.

>>>You may need to clear the CMOS ROM by pulling the battery.<<<

I did that already...that's when I lost the f10 option to get into the bios...I did that to fix a 1782-disk controller failure- error message...fixed it, but lost the bios...:(

Is there a reputable site where I could get my bios flashed right?

---

### Post by dmizer on 2006-09-19
your compaq does not have hdd based flash.  it has a flash chip.  you would have needed to do something major to "un-flash" the bios.  something else is wrong.

furthermore, you would not be able to boot to anything (including the cdrom drive) if your bios was not working or absent.

since you say you've already had the cover off to pull the cmos battery, are you sure:

1) ide cables to the hdd are in place correctly (both ends).
2) ide cables are not in upside down? (this can happen on some older ide cables)
3) are you using cable select cables? and ...
4) jumpers for the hdd and cdrom are in the correct place.
5) power cables to the hdd are seated correctly.

---

### Post by xpod on 2006-09-19
Just to let the guy know i have a compaq presario too but it`s a different model No so not sure just how different they are..5130 mines is.

There aint no bios "partition" on it and i had to remove it`s battery today just to get by it`s password that had been set...
Dont know if removing your battery would have any bearing but you have to be really careful with static and the like.

Mines was a bit tempramental after reboot but after a few more reboots it eventually spluttered back to life.
f10 was the bios key on iy btw.

Hope you sort it out

---

### Post by dizzylizard on 2006-09-20
> **dmizer said:**
> your compaq does not have hdd based flash.  it has a flash chip.  you would have needed to do something major to "un-flash" the bios.  something else is wrong.

furthermore, you would not be able to boot to anything (including the cdrom drive) if your bios was not working or absent.

<<<not to dispute you, but isn't the program for the BIOS interface stored on the hdd?  just what I picked up from a compaq forum.>>>

since you say you've already had the cover off to pull the cmos battery, are you sure:

1) ide cables to the hdd are in place correctly (both ends).

<<<In and tight...the first thing i checked>>>

2) ide cables are not in upside down? (this can happen on some older ide cables)

<<<not possible with my cable>>>

3) are you using cable select cables? and ...

<<<how do I tell?>>>

4) jumpers for the hdd and cdrom are in the correct place.

<<<have them all set to cable select>>>

5) power cables to the hdd are seated correctly.

<<<seated and tight>>>

any other suggestions?  I've tried reinstalling Ubuntu, to no avail...BTW, thank you for helping a lowly newbie...I've been wrestling with this box for 2 weeks or so now...it's a frankenbox built from parts...worked fine with mandrake community 10.1...upgraded to Mandriva free 2006 (buggy...couldn't access internet)...tried to install Ubuntu and lost my HDD...any ideas?

---

### Post by dmizer on 2006-09-20
> <<<how do I tell?>>>
if you have cable select cables, the ide cable will be labeled as such. you will see "cs" or "cable select" written on it somewhere.  if not, you shouldn't have your jumpers set to cable select.

also ... if your cable IS cable select (which is likely if you haven't touched your jumpers), you will have to make sure that the drives are connected in the correct order.  ie, most likely, the cdrom connects to the middle plug, and the hdd plugs into the end.  the ide cable connectors will also likely be labled as "0" and "1", or "chanel 1" "chanel 2".  the lower number will need to connect to the hdd, and the higher number will need to connect to the cdrom.

if all above is okay, perhaps the drive has given up.  if you have a spare sitting around (even a very small drive) pop it in and try it to see if it will get detected.

> <<<not to dispute you, but isn't the program for the BIOS interface stored on the hdd? just what I picked up from a compaq forum.>>>
ancient ... and i mean VERY ancient compaqs and other computers sometimes had bios interface on the hard drive.  i'm not aware that they are still doing that.  you might provide a link to the forum where you saw this information, it might give us something to go on if it pertains to your computer.  remember, bios stands for basic input output system.  it controls basic functionality of your computer.  if you can boot to your cdrom, your bios is working correctly.

we were all noobs at one time or another. no reason to consider yourself lowly.

---

### Post by dizzylizard on 2006-09-21
well...apparently the 'puter gods have smiled on me...after making my last post, I rebooted, re-installed the CD, and it works fine...I don't know what i did...but it worked :)...Thank you all for all your help...
Damien

---

