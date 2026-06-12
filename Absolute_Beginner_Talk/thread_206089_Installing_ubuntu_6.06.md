---
title: "Installing ubuntu 6.06"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Supa_no1 on 2006-06-29
Hiya i have just burned ubuntu 6.06 to a cd disk and when i restart the computer it wont boot off of it! At the moment my hardrive is empty and i am running the computer off a ubuntu disk i got a long time ago. i want ubuntu to be saved to my hard drive but it wont boot off the cd rom! please help!

---

### Post by myfootsmells on 2006-06-29
you might want to go into your BIOS and double check that the first boot device is your CDROM drive.

---

### Post by Supa_no1 on 2006-06-29
Tried that! What else?

---

### Post by Supa_no1 on 2006-06-29
on the cd should there just be the .iso file?

---

### Post by johnc4510 on 2006-06-29
If you are running the computer now off a older disc, then I assume you booted from that disk. If so, then we know that your computer will boot from disk. So I have to believe that there is a problem with the new cd or the burning of it. You can try burning to another cd, and when you do, slow the burn speed way down. These iso's are suppose to be burned slowly.

---

### Post by tonyr on 2006-06-29
[QUOTE=Supa_no1]on the cd should there just be the .iso file?[/QUOTE]

hmmmm.... How did you burn the CD?  Did you use the option that says something
like "Burn iso image", or did you make a new data project?

---

### Post by Supa_no1 on 2006-06-29
is there any other reasons?

---

### Post by Supa_no1 on 2006-06-29
i did it round my friends house using windows. we made it into a image disk  i think

---

### Post by ifican on 2006-06-29
I have to respectfully disagree with the addage that iso's need to be burned slowly, its all simply data and i have never had a problem burning iso's at any speed. Back to this issue however, i am in agreeance that mostlikely this was burned to the disk directly how it was d'led as the iso file not the bootable image. Reburn the iso as an image and you should have no problems booting.

---

### Post by stychman on 2006-06-29
If you open the disc in Windows is there one file that is an ISO or are there a bunch of files on the disc?  Also, the disc should autorun in Windows and bring up a browser to install Open Source Software for Windows.  Does this happen?

---

### Post by Supa_no1 on 2006-06-29
the disk only shows one file which is called ubuntu-6.06-server-i386.iso

---

### Post by Supa_no1 on 2006-06-29
the disk only shows one file which is called ubuntu-6.06-server-i386.iso

---

### Post by tonyr on 2006-06-29
[QUOTE=Supa_no1]is there any other reasons?[/QUOTE]
The file you downloaded could be bad.  DId you do the checksum thing on it?
The place you downloaded it from should have had a file called MD5SUMS
or something like that.  There is a program in Windows that you can use to
do a (md5) checksum on the downloaded file.  The checksums should match.
If they don't,  bad news.

I've also heard of burns just not working at all.  Did you use the **verify** option
when you burned it?

---

### Post by Supa_no1 on 2006-06-29
on the disk should the iso file be extracted or not?

---

### Post by tonyr on 2006-06-29
OK, you definitley burned the CD the wrong way.  You should not see any .iso
file on there at all.  You will need to burn the CD again and make sure you
select "Burn iso image".

---

### Post by ajgreeny on 2006-06-29
Did you specifically want the server edition or do you want a desktop edition?

If you want a desktop to run download the ubuntu desktop iso and burn that as an image.  If you have no good windows burning software, get a copy of cdburnerXP, its freeware and excelent at burning images to disk.  Google will find it easily for you.

---

### Post by Supa_no1 on 2006-06-29
i want the edition which is permenantly on your computer and i am using ubuntu 2.06 atm

---

### Post by ajgreeny on 2006-06-29
What I meant was, do you want a graphical interface or to do everything at the console by typing commands?  I you want a GUI then you need the ubuntu desktop version as the server will not have any graphical interface for you to use.  Once you have installed the desktop version to your hard disk it will be there permanently.

You still need to burn the iso file to CD as an image, not just copying it to CD as you would if you were backing up files.

---

### Post by Supa_no1 on 2006-06-29
i want the graphical interface so what do i download and how do i burn it?

---

### Post by tonyr on 2006-06-29
Here is a link to a complete set of instructions:
[http://psychocats.net/ubuntu/iso.html]("http://psychocats.net/ubuntu/iso.html")

---

### Post by underdog on 2006-06-29
[QUOTE=ifican]I have to respectfully disagree with the addage that iso's need to be burned slowly, its all simply data and i have never had a problem burning iso's at any speed. Back to this issue however, i am in agreeance that mostlikely this was burned to the disk directly how it was d'led as the iso file not the bootable image. Reburn the iso as an image and you should have no problems booting.[/QUOTE]

Yes, it is all data, but if you go too fast, it will get messed up. Just google it, you will see many people have had problems with isos burned too quickly.

---

### Post by ifican on 2006-06-29
As was figured this appears to be a incorrect burn not a speed issue, and on that one, yes many folks have had issues. But i have personally burned several hundred iso's for different things and the only time i have had issues that slowing down helped was when i used cheep cd's (most probably the cause for all the complaints), specifically GQ. When using any quality CD i never have any issues at 48x (fast any my burner goes) burning iso's. 

As far as this one is concerned, yes cdburnerxp is a great little program, it can be a little confusing though initially. When you open the program simply choose the top of the 3 options which is the one to burn iso's. The go to file>write cd image from iso (or something very similar to that). Locate and select the iso image and make sure you select the option to finalize the CD. Be patient at the end at it will show 100% complete but sometimes it takes about 90 seconds to finish. Once done you should be good to go.

---

### Post by richbarna on 2006-06-29
With Nero on Windows, you just right click the .iso file, select open with... Nero, and it does the rest, you just have to click "Burn".

As for High-Speed burning of isos, I am against it. I too have burned hundreds on good cd's and will always go for 4X if available, or 8X.

---

