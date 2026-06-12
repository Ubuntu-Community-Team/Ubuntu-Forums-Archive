---
title: "How stupid? Can't even get installed"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2006-05-05
OK,
I'm trying to dabble with Ubuntu and I can't even get installed!

I've downloaded 5.10 and get half way through the installation and I simply don't understand how or where to install the software.

I have a spare partition on my 120 GB hard drive of about 12GB, which I understand should be big enough to start.

During the installation process I select manual partition configuratio or whatever.  I then seem to go round in endless loops.  I point to the empty 12GB partition (NTFS) but every time I ask to install there it goes back to the partition manager part of the installtion package.

I've searched around Ubuntu.com for about two hours and can't even fird any basic instruction how to install the basic package.


I'm confronted with menus that ask me questions about formatting that I have no clue in answering.

I'm a very experienced Windows user and have installed Windows OS from 3.1 up to my current XP Pro.  I was also comfortable with DOS so am not phased by the CLI.

Why can't I even get passed the installation?  Am I so really thicK?  Is Linux for me?

I'm keen to learn, please help.

Thanks folks.

---

### Post by bt224 on 2006-05-05
I can't help, other than to say don't give up. I've been struggling for a few days but things are getting easier and easier. You will get terrific help and support here to help make sure you are successful. And so far it's been fun to learn.

---

### Post by o_fortuna on 2006-05-05
[QUOTE=Phosphoric]OK,
I'm trying to dabble with Ubuntu and I can't even get installed!

I've downloaded 5.10 and get half way through the installation and I simply don't understand how or where to install the software.

I have a spare partition on my 120 GB hard drive of about 12GB, which I understand should be big enough to start.

During the installation process I select manual partition configuratio or whatever.  I then seem to go round in endless loops.  I point to the empty 12GB partition (NTFS) but every time I ask to install there it goes back to the partition manager part of the installtion package.

I've searched around Ubuntu.com for about two hours and can't even fird any basic instruction how to install the basic package.


I'm confronted with menus that ask me questions about formatting that I have no clue in answering.

I'm a very experienced Windows user and have installed Windows OS from 3.1 up to my current XP Pro.  I was also comfortable with DOS so am not phased by the CLI.

Why can't I even get passed the installation?  Am I so really thicK?  Is Linux for me?

I'm keen to learn, please help.

Thanks folks.[/QUOTE]
Here's what you have to do: Your "spare" NTFS partition has to be TOTALLY reformatted, meaning any data on that partition will be lost. Linux cannot install on NTFS. Basically, in the partition manager, delete that 12GB partition, which should leave you with 12GB of free space. Then, once you have that, go back and tell it to automatically partition using free space. If you have trouble, just ask.

---

### Post by nanotube on 2006-05-05
here is what you should do
**delete** the ntfs partition, so that the 12g shows as "unpartitioned space"
then select it, and choose the "automatically partition unpartitioned space" option
that should get you over the hump. :)

(this is because you cant install linux on ntfs partition)

---

### Post by opus on 2006-05-05
Did you select and empty 12 GB partition or did you create the 12GB partition?

Try deleting the partition and recreate it.  When asked about formatting, choose ext3 (why? because it's a good file system, and it doesn't matter that much.  I personally use ReiserFS).  You also need to select the mount point - you want it mounted under "/".  

That should do it.  I'm sure you will have additional questions, so fire away.  :)

Aaron

---

### Post by bluevoodoo1 on 2006-05-05
[QUOTE=Phosphoric]OK,
During the installation process I select manual partition configuratio or whatever.  I then seem to go round in endless loops.  I point to the empty 12GB partition (NTFS) but every time I ask to install there it goes back to the partition manager part of the installtion package..[/QUOTE]

You won't be able to install it to an NTFS partition, it cannot be written to by Ubuntu (only read). Try using the ext3 type.

Question: Are you going to have windows on that computer as well? If so, install windows first, then Ubuntu. For that, check out this useful link...
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Phosphoric on 2006-05-05
Right, now I'm really in trouble.  Posting on another PC.  

After trying to configure this spare partition to install Ubuntu, it failed half way through.....Base system installation error.....

On reboot I get after the normal "Verify DMI Pool Data"
Boot from CD:
NVidea Boot Agent 211....
Copyright .......
Client MAC ADDRR XXXXXXXXXXX
DHCP...............

then it hangs for ages and eventually comes up with:
PXE-E53: No boot filename received
PXE-MOF: Exiting NVIDEA Boot Agent
DISC BOOT FAILURE, INSERT SYSTEM DISC AND PRESS OK.


Well,  I've tried resetting the BIOS by clearing the CMOS in the usual way, even took the battery out.  Set the boot order to Foppy, IDE, then CD ROM, all to no avail.  
 I seem to have lost my Windows Boot Up.  Now I know you guys are a bit anti M$ but come on, I'm absolutely stuffed now.  One of those jobs you just wish you never started!

Help please.

---

### Post by catlett on 2006-05-05
Put in your XP install disk or a recovery disk that came with your computer. Boot to recovery mode, When you get to the command line type ```
fixmbr
```
This will rewrite yourMBR and windows will boot.
If your still interested follow the link in my signature for a how to.

---

### Post by Phosphoric on 2006-05-05
OK tried the fixmbr trick, didn't work.

I'm starting to panic now.  I seem to have lost my Windows XP along with all my data.

How could Ubuntu do this to me?

I'm now completely stuffed.

Help PLEASE.

---

### Post by catlett on 2006-05-05
That's bad. If XP was there fixmbr would boot. Only your 12gb partition should have been formatted. You would of had to select "erase entire drive" for it to have touched your other partition.
It appears you can boot into a cd. Do you have the Live CD of Ubuntu? Or any linux live cd, I ask this because with a live cd the cd replaces your hard drive and the operating system operates off the cd. What this can do for you is get your computer running under linux and then we'll try to mount your windows partition and see if your data is there.

---

### Post by catlett on 2006-05-05
> DISC BOOT FAILURE, INSERT SYSTEM DISC AND PRESS OK.
Did you try getting to this point again and inserting your XP install disk (or your computer recovery disk) to see what happens when you hit OK?

---

### Post by n3tfury on 2006-05-05
[QUOTE=Phosphoric]

How could Ubuntu do this to me?

[/QUOTE]

Don't blame the OS.  Maybe you should have taken a look at one of the many guides on the 'net.  Sounds to me like you were winging it.

---

### Post by mips on 2006-05-05
I would not blame ubuntu.

If you only formatted the 12GB partition then I honestly don't think you have lost your data.

Have you got a LiveCD like Knoppix or Ubuntu ??? If not get one.

This way we could check and see if your data is still there. and maybe fix the situation.

I'm off to bed for now...

---

### Post by mips on 2006-05-05
[QUOTE=catlett]Did you try getting to this point again and inserting your XP install disk (or your computer recovery disk) to see what happens when you hit OK?[/QUOTE]


From the recovery console there is also a fixboot command, dunno what it does, help gives you a list of all available commands.

---

### Post by alphaomega on 2006-05-05
Try this with your XP recovery cd.  When it boots up to the setup screen, press R for recovery. You should see a C:> in a few. Type CHKDSK and press enter. If there are any errors on your harddrive it will tell you. After it runs type HELP. It will list a bunch of commands. There will be one I think called FIXBOOT or something close, that should work. If not, I think you might need Hirens Boot Disk to see what the matter is with your partitions and recover your files.

---

### Post by az on 2006-05-05
[QUOTE=Phosphoric]
During the installation process I select manual partition configuratio or whatever.  I then seem to go round in endless loops. .[/QUOTE]

That's because you are not doing what it is asking you to do.  Mind you, the instructions are obtuse, but you are told to create at least a / and a swap partition, which means getting rid of the ntfs partition and creating an ext3 (or some other filesystems) one.

Had you not picked manual partitioning and just let it automagically do the partitioning for you, you would already by enjoying Ubuntu right now.

---

### Post by skippy81 on 2006-05-05
If the data which was on your windows partition is important to you, then you are going to need to get a functioning PC in order to work out what went wrong.

If you have accidentally deleted your Windows NTFS partition then all is not lost.  You need to transfer that harddisk into an other PC, jumpers set up as slave.  You then will want to run some recovery software on it.  You will probably get most of the data back providing the disk was fairly big and the data wasn't too fragmented.  

If you are lucky then the partition is still there and active and you have only lost the mbr, in which case you will be able to retireve your data off it without any difficulty.

Either way, you want to physically remove that hard disk and mount it as a slave in a working PC - keep your head and don't get wound up.  Testdisk and PC Inspector are both decent free data recovery proggys.

Next time I suggest you make a backup before you attempt to install any kind of operating system in a dual boot config.  This rule goes for linux, windows or anything else.  Any task which involves rewriting the partition tables carries a certain amount of risk - the newer you are then the more important it is to back up first.  Partitioning disks is like anything else in life, it takes practice and time to become proficient at it.

---

### Post by Phosphoric on 2006-05-06
OK, I'm back up and running again. :grin: 

Thanks for the repiles and suggestions.

Fixmbr didn't work neither did fixboot

I got it back from a 3 month old backup of Acronis True Image.  Having got a bootable windows OS I was then able to restore my C Drive from a backup that I made to an external drive immediately prior to trying to install Ubuntu.

So, where did I go wrong in the installation?
I did search for some time to find a step by step instruction but the only "how tos" I found were for installing applications from with Ubuntu.

Azz, the reason I selected manual partition selection was so that I could install on to an empty 12GB partition that I made available.  In automatic mode, it appeared to me that the installer wanted the whole drive.

If somebody could point me to a blow by blow installation guide I'll have another go when I've recovered a bit!

Thanks :D

---

### Post by steve.horsley on 2006-05-06
That's a relief! Good job you had a backup.

I've seen the suggestion before, but let's say it again. Use a partition editor that you are familiar with to delete the 12G partition that you want to install Linux on. Don't just format it, delete it so it is unused disk space. Now the installer should offer you an option of either erasing and using the whole disk (which you don't want), or using the free space. Just tell it to use the free space and let it do its own thing. It will actually create two partitions - an EXT3 partition for the system and a small swap partition for use as virtual memory.

If you don't get the offer of using the free space, there is something wrong. In which case, running up a "live" Linux CD - one that runs linux without touching the hard disk - may be useful so we can see what the partition table really looks like. The command to do this is > fdisk -l (that is an ell - lower-case L at the end.) If using an Ubuntu live CD, you may have to say **sudo fdisk -l** instead.

Good luck. And it is probably less stressful to come back here and ask than to forge ahead unsure and have to restore backups again, so feel free to come and ask.

---

### Post by talltree on 2006-05-06
Yes, it is a bit confusing, not to mention other things you are unaware of as yet. One thing I might recommend is that you divide your drive into three partitions. (This is what I did.) One for your Microsloth Windows, one for your Ubuntu, and another for a Ubuntu swap file. For instance, I made a 10 gig swap, then divided the rest of my disk equally for Windows and Ubuntu. (This was a 60 gig drive.) I might add that you continue to rely on Windows (As much as I hate it and the Blue Screen of Death!) for your main OS and explore Ubuntu. Any Unix based system is more complicated than Windows and requires a very steep learning curve. Particularly as you have to have command line knowledge. Or from the prompt, as you would know it, in DOS. However, once you get the hang of it, you will never go back to windows. I have never had my systen crash, or lock up, since I installed Ubuntu. That is certainly not something that ANY Windows system can claim.

---

### Post by Phosphoric on 2006-05-06
OK, cooled down a bit now and followed the advice in Catletts signature (thanks mate) for dual booting and I'm almost there with no drama.

Just got to find a way to get this xserver thingy to work, at the moment i get dumped out to the CLI.

Off hunting! :razz: 

Cheers

---

### Post by n3tfury on 2006-05-06
[QUOTE=Phosphoric]

So, where did I go wrong in the installation?
I did search for some time to find a step by step instruction but the only "how tos" I found were for installing applications from with Ubuntu.

[/QUOTE]

[Keywords and Google can be your friend]("http://www.google.com/search?q=ubuntu+installation+guide&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official")

---

### Post by r4ik on 2006-05-06
From the command-line type youre usrname and passwwrd hit enter.
Do a,

sudo dpkg-reconfigure xserver-xorg   and hit enter,

just follow the defaults until you get to youre grapics card section select "nv" for Nvidia or "vesa"

continue and finish with,

sudo /etc/init.d/gdm stop  =>enter

sudo /etc/init.d/gdm start  =>enter

Good luck !

---

### Post by Phosphoric on 2006-05-06
Hi,
here I am typing this in in Ubuntu.:D 

Thanks everybody for their help, I now realise I'm at the bottom of a very steep learning curve.

Will it be worthwhile?  Only time will tell.

Off to get my printer working now.  Cheers.

---

### Post by catlett on 2006-05-06
Thank god for backups. I was worried. I can only imagine how you felt because it was your data.
What you have to realise is windows and linux is apples and oranges. Just because they'r both fruit doesn't mean you core them the same way.
After you learn Linux you'll love it. You can do so much more. I've gone from worrying about this fragile thing I use, not wanting to do too much or change anything because it might freeze up. To feeling like I have limitless resources. I thought changing a theme was a big deal in windowes in linux I can change window managers.
If you want to try kde out (now you're using gnome) open the terminal and type ```
sudo apt-get install kubuntu-desktop
``` This will install the kde desktop alongside gnome. When you log on you can click on sessions and choose between kde or gnome.
In the mean time here are a few usefull links [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html) ... [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) ... [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles)... [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by nanotube on 2006-05-06
[QUOTE=talltree]Yes, it is a bit confusing, not to mention other things you are unaware of as yet. One thing I might recommend is that you divide your drive into three partitions. (This is what I did.) One for your Microsloth Windows, one for your Ubuntu, and another for a Ubuntu swap file. For instance, I made a 10 gig swap, then divided the rest of my disk equally for Windows and Ubuntu. (This was a 60 gig drive.) [/QUOTE]
ehrm... 10g swap is Really overkill. there is no way more than like, 1g, will ever get used - you are essentially wasting 9g of hd space. 
just a piece of advice for you for the future. :)

---

### Post by mips on 2006-05-07
[QUOTE=nanotube]ehrm... 10g swap is Really overkill. there is no way more than like, 1g, will ever get used - you are essentially wasting 9g of hd space. 
just a piece of advice for you for the future. :)[/QUOTE]

Good point, 1GB should be more than enough. I have 1GB ram & 2GB swap, at this very moment the swap is not even being used...

---

### Post by Phosphoric on 2006-05-07
I> n the mean time here are a few usefull links [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html) ... [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) ... [http://pykeylogger.sourceforge.net/w...ntu:Chronicles](http://pykeylogger.sourceforge.net/w...ntu:Chronicles)... [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Catlett, many thanks for those links, they are brilliant.
I got my printer working within 5 minutes of opening one of the links. :D 

Thanks again all those with helpful suggestions.

I think I'm going to like it here.:D :D

---

