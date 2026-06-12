---
title: "Ok, Ubuntu is not right for me...please help."
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Ubun2User on 2007-11-04
Okay so Ubuntu is for people with more computer knowledge and time than me.  I need to remove Ubuntu and remove the partition on my Hard Drive so that all of my HD space is allocated to Vista...please help.

Thanks!

---

### Post by wieman01 on 2007-11-05
You might want to try a Windows support forum... ;-)

Do you own Partition Magic by chance? Nice Windows program which lets you reformat and reallocate space.

To get rid of GRUB I would suggest an old Windows 98 boot CD so that you can reformat the MBR. Do you know how to do that?

---

### Post by -grubby on 2007-11-05
sorry it didn't work out...you're going to have to load you're Ubuntu live-CD and navigate the menus to "gparted" or "GNOME partition editor" (can't remember the name right now) and format you're Ubuntu partition to FAT32 (best for Windows to understand) and then resize your Vista partition. 
EDIT: oh yah, if you have a windows XP CD (maybe works in Vista DVD?) enter recovery mode and type "fixmbr" (to fix the bootloader)

---

### Post by HermanAB on 2007-11-05
Basically, you need to use gparted to delete the Ubuntu partitions to a single partition and then make it NTFS.  From Windoze, you can then access it as Drive D:.  I don't think you can successfully 'grow' a NTFS partition to re-absorb the freed space, but I may be wrong.  Aanyway I won't even try - too dangerous - rather make it drive D:.

BTW, Ubuntu is one of the more difficult versions.  If you want an easy to use Linux, that will run extremely fast right off a CDROM, see this: [http://puppylinux.com/](http://puppylinux.com/)

Cheers,

Herman

---

### Post by avik on 2007-11-05
> **HermanAB said:**
> BTW, Ubuntu is one of the more difficult versions.  If you want an easy to use Linux, that will run extremely fast right off a CDROM, see this: [http://puppylinux.com/](http://puppylinux.com/)

Actually, I would say Ubuntu is one of the easiest distributions you can find.  The community is helpful, and you can get paid support.  Once you get used to a couple of new things (installing packages instead of downloading installers, etc), it's no big deal.  If you don't have any computer knowledge, Ubuntu is definitely the way to go.

Still, I understand GNU/Linux in general is not the right choice for everyone.

---

### Post by tempest on 2007-11-05
I am not familiar with the Vista installer, but have installed XP more times than I care to remember. The XP installer always had an option to remove all of the existing partions and create a new partition to install Windows onto. I cannot imagine that M$ would have removed that option in the Vista installer, but I could be wrong.

---

### Post by Can+~ on 2007-11-05
I think gparted can format to NTFS (which window$ can read). So it would be easy to jack up the LiveCD and format to NTFS.

---

### Post by wieman01 on 2007-11-05
> **Can+~ said:**
> I think gparted can format to NTFS (which window$ can read). So it would be easy to jack up the LiveCD and format to NTFS.
Last time I tried it couldn't. But that was on Feisty.

---

### Post by itix on 2007-11-05
Oh what the hell, just as you normally would use windows and it'll sort out. I'm no computer genius either, but I get along with Ubuntu. You'll learn.

Just a piece of advice though if you did change your mind. DONT CHANGE ANYTHING YOU DONT KNOW WHAT IT IS!

---

### Post by evets on 2007-11-05
> **tempest said:**
> I am not familiar with the Vista installer, but have installed XP more times than I care to remember. The XP installer always had an option to remove all of the existing partitions and create a new partition to install Windows onto. I cannot imagine that M$ would have removed that option in the Vista installer, but I could be wrong.

Most folks I know who want to move away from MS, and aren't sold on Ubuntu/Linux, wind up with a Mac. You might try one, they are very nice, very user friendly, and later on, you can get into the "guts", which is Unix based.

Yes, use either your Vista or XP CD to remove grub. Select R for repair, and then type fixmbr in the console, and you'll get a message saying a new MBR was successfully written, then type exit, and reboot. 

Whether or not you can resize your partitions with MS depends on a few things, most notably the "Edition" you own. You'll need the "Pro"edition or it's equivalent on Vista. Go to Start>Run, and type in diskmgmt.msc and hit enter. There you will see your drive(s), and you can manage them from there.

Good luck.

---

### Post by Virgofenix on 2007-11-05
> **wieman01 said:**
> 
To get rid of GRUB I would suggest an old Windows 98 boot CD so that you can reformat the MBR. Do you know how to do that?

I'm wondering how that's done. Can that be done using the Windows XP CD?

---

### Post by wieman01 on 2007-11-05
> **Virgofenix said:**
> I'm wondering how that's done. Can that be done using the Windows XP CD?
Yes, it apparently can. There are other posts in this thread that outline just that. Read them first.

---

### Post by linaxe on 2007-11-05
Well right now ubuntu is tough i wont to install java on ubuntu 7.04
if u can help plz do:confused:

---

### Post by Kurenai0h on 2007-11-05
Waah, I need to do the same thing, but when I put in my XP CD on my new Vista pc and type E to enter the console it ask first for a nr to login into then a admin password, and I have no idea what that is! Where can I find it?

---

### Post by Presto123 on 2007-11-05
> **linaxe said:**
> Well right now ubuntu is tough i wont to install java on ubuntu 7.04
if u can help plz do:confused:

Do a search on "Add/Remove" showing "All Available Applications", type in "ubuntu restricted". Read through the information before you decide whether to install, and if you agree to install, then restart the computer after it is finished. Then you can go back to the "Add/Remove" and type in "Sun Java 6" and it should either show up as checked (Installed) or not, if not, you can install it if, yet again, you agree to the information.

---

### Post by Virgofenix on 2007-11-05
> **wieman01 said:**
> Yes, it apparently can. There are other posts in this thread that outline just that. Read them first.

Thanks. My bad.

---

### Post by CivDevil on 2007-11-05
Whatever you do, please don't try to use GParted (Ubuntu's partition utility) to 'grow' your HD/resize your NTFS partition.  36 hours of unmitigated !#$ taught me that this method does not work.  Follow the previous suggestion and leave the partition intact as a separate logical drive (D: for example).

---

### Post by SunnyRabbiera on 2007-11-05
Well i promise you in the long run Vista will be just as bad...
with all its restrictions and bull...

what do you find so hard in linux that is making you want to go back?
If you had problems you should have asked...
enjoy the blue screen of death.

---

### Post by barkej on 2007-11-05
Sorry to see you go. Linux is not for everyone, I hope you decide to give it another chance in the future as development is very fast and things change all the time.

Ask for help if you have trouble while using linux.

---

### Post by SunnyRabbiera on 2007-11-05
you know you can easily try another distribution, if ubuntu doesnt work for you you dont have to say all linux sucks...
you can try other versions, like PClinux, Mandriva, even those microsoft sellouts suse.

---

### Post by Arthur Archnix on 2007-11-05
It's not that complicated.  From another [thread]("http://ubuntuforums.org/showthread.php?t=463534&highlight=Ted+Nancy"),


> Listen to the caution from LuisB above. Do not delete any partitions without first making sure Vista boots normally.

I had a similar problem. An OEM vista disc from HP, no restore partition to work with, and no desire to just restore factory default.

Here is what worked for me:

Download MbrFix.exe from [www.sysint.no](www.sysint.no) (click the downloads link, and read over the readme link beside the download link to the file.)

Then do from Vista:

>Start >Accessories and right-click "command prompt" and then choose "run as administrator"

Then type (without quotes):

"MbrFix /drive 0 fixmbr /vista"

And reboot. Grub should be gone and Vista should boot normally. If not, you'll have to review the documentation. It could be that drive should not = 0.

Once Vista boots normally, go to control panel and use the disk management utility to delete the non-windows partitions. Reboot again. Then use the same utility to expand the Vista partiiton to full size of hard disk.

---

### Post by tdmoore on 2007-11-06
I have a similar issue as per another post of mine.

evets...I assume this will delete all files and apps if I follow your instructions here?

Or does it just repair the MBR and I am back into Windows properly?

---

### Post by Ubun2User on 2007-11-21
Okay i never uninstalled Ubuntu...man am i glad I didn't.  I can't stand Vista and cuz I can't get Mac OSX on this machine, I am going to stick it out.

Can't wait to learn more!

---

