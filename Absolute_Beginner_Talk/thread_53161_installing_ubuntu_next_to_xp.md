---
title: "installing ubuntu next to xp"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by taky on 2005-07-30
Hello,

I'm new to this, I hope I can get some guiding here on how to get ubuntu installed.
Situation is the following:

I have the Ubuntu 5.04 cd , I have a hard disk which has 2 partitions, on C: i have xp home, dutch version which i had for the kids, and on the D: I have xp pro english version.
I would like to keep the D: xp pro, and install ubuntu on the C:, cause I dont need that xp version anymore..

I had put in the Ubuntu cd, and restarted the pc, but then I had no idea what option to choose, I certainly don't wanna loose the D:...anyone can help me how to do this?
Or is this not possible with this linux version?

Anyhow thanks :)

---

### Post by Larkki on 2005-07-30
I guess it should be fairly easy to do.
First, find out what what are the sizes of the partitions C: and D: so you can identify them in linux installation. Linux doesn't name them as C: or D: anymore.

When you start the installation and ask to the questions about language etc, you get to the partitioning part.
Choose manual partitioning, and then it shows you the list of partitions you have on your system. Now you remember the size of your C:-drive? Choose that drive, make it to use "ext3 filesystem", choose to format it, make it bootable and assign it as / (root). All those choices you make in the partitioning part of the installation. After making the choices, select "Write the changes to disk" or something like that, then it should format the drive and start installing Linux to your C:
After all the file copying, it might ask if you want to make a boot loader to your master boot record, and it shows you the already available windows system(s). Choose yes, and it will create a GRUB loader, where you can choose if you want to start windows or linux.

I hope everything goes well. For my first computer everything went fine, for my second it didn't. But I had a RAID system on it. Good luck.

---

### Post by taky on 2005-07-30
thank you, let's hope all goes well  :|

---

### Post by taky on 2005-07-30
Have another question.you said to choose "Ext3 file system"...but I have the choise either: Ext3 journalling file system, or Ext2 file system...which should I choose?

---

### Post by aysiu on 2005-07-30
[QUOTE=taky]Have another question.you said to choose "Ext3 file system"...but I have the choise either: Ext3 journalling file system, or Ext2 file system...which should I choose?[/QUOTE] Ext3

---

### Post by taky on 2005-07-31
It went wrong...ubuntu installed fine, but at the end where it should install the grub bootloader, i got the 'fatal error message' says can't writ it to disk....so ended up not being able to boot at all anymore, not even the windows partition.
Using my sons pc now...anyone got an idea what went wrong, how come i couldn't  write the grub bootloader?

---

### Post by Xian on 2005-07-31
[QUOTE=taky]Using my sons pc now...anyone got an idea what went wrong, how come i couldn't  write the grub bootloader?[/QUOTE]
That happens to me a lot. The fix on my system was to return to the Install Menu on the CD and choose once more to install Grub. It will go through the same process but on the second attempt it generally works. You could also install Lilo instead using the expert install mode.

---

### Post by Irony on 2005-07-31
You can restore the XP bootloader;

Boot from XP installation disc > press any key on prompt to boot from CD > after some time options appear, press R for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc

Now boot up into the XP version you want to keep. You can then delete the XP partition you don't want. Go;

Start > Programs > Accessories > Device Manager > Computer Management

I can't remember the exact route here because I'm in ubuntu at the moment, but you are looking for the option in Device Manager which shows the partitions on your drive. It looks something like this;

[http://www.ironclub.net/log/part2.png](http://www.ironclub.net/log/part2.png)

Now right click on the partition that contains the XP you don't want and select delete partition, it will now say unallocated space. This may mess up you windows bootloader again but this doesn't matter because you put you ubuntu disc in and then shutdown as normal.

The reason for doing this is to create a big free space for the ubuntu installation.

Now switch on to install ubuntu. Select the free space and automatic partition option when they arrive. This saves the hassle of trying to determine swap partition sizes and format options.

I'm still new to ubuntu and linux myself, but this method worked on both my laptop and desktop.

---

### Post by Larkki on 2005-08-01
Too bad it didn't go straight as planned.
Irony's way is probably the best to recover your windows. Let's hope you can do that.
If you still want to try ubuntu, maybe the 2nd try works, no idea on that. You can also try to install to another HD and install the Grub loader on that other HD (same where you install the linux). If you do this, then you must change the Boot order in BIOS, so that the Hard Drive which has the GRUB boot loader, is first drive to boot. (You should check your bios first if it has this option. New BIOS usually does. Press [del] or F9 or F10 when your computer is starting up to enter the bios. Depends on computer.)

---

### Post by taky on 2005-08-01
[QUOTE=Irony]You can restore the XP bootloader;

Boot from XP installation disc > press any key on prompt to boot from CD > after some time options appear, press R for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc

[/QUOTE]
Tried that, but still could not get to boot my xp again..., also tried several times to install the grub..didn't work either....already reinstalled xp...will try again later to do the ubuntu... ](*,)

thanks everyone for the replies :)

---

### Post by isTHEr3mOr3 on 2005-08-01
If you don't mind to install another distro, you could try Suse. 
Suse is very good in detecting and automatic installation next to XP

[My blog](http://tlinux.blogspot.com)

---

