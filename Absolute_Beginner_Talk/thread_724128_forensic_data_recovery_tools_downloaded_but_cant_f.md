---
title: "forensic data recovery tools downloaded but cant find"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by slick1a on 2008-03-14
I need some assistance with this one ...here goes:

Returned from ireland with 172 jpeg's of the weekend . I cut these from the cameras XD 2gig card and pasted them to my external 320gig H/D for future reference. that nite my wife and I reviewed all the images and had a great laugh.   I then tried to make a copy for a few of the boi's I travelled to ireland with , however when i tried to open the folder containing said jpegs i got the message CANNOT DISPLAY FOLDER CONTENTS....thats the background.

What I have tried so far: 

1. searched for file named piks/ireland  CANNOT DISPLAY FOLDER CONTENTS
2. plugged external HD into a windows machine got the same error
3. trawlled google and forums came up with :[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org) Ubuntu Rescue Remix is a GNU/Linux live cd that provides the data
recovery expert with a command-line interface environment equipped
with the best free-libre, open source data recovery and forensics
tools available.
4. Nothing seemed to work. Finally, I discovered TestDisk and PhotoRec,

Having installing the above Im unable to locate to app to use it  THIS IS WHAT I NEED HELP with.

I know theres 172 images but where are they ?   A cry for help shouted at the highest point of the highest mountain, must be heard by many.

---

### Post by ruy_lopez on 2008-03-14
First of all, DON'T mount the drive again, until you can be sure it is mounted read-only.

What kind of drive is it? Do you know what type of filesystem it uses (ext3, ntfs, fat)? Have you used the drive much (lots of files created/deleted over time?)?

I might be able to suggest some things to try, but I need to know more.

---

### Post by bumanie on 2008-03-14
Your best bet is to try photorec from here
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
Good Luck.

---

### Post by ruy_lopez on 2008-03-14
Foremost is also good, but it's results tend to vary with disk fragmentation.

---

### Post by slick1a on 2008-03-14
fantasic some new things to try ..many thanks 

My external HD has many things on it and has never been formatted but used on many many machines , both windows and linux, many deletions and additions.

Its in ntfs format , everything else can be read/written /cut or copied apart from the missing contents of my 'ireland' folder which as you can appreciate having such a great time away with the bois is most annoying not being able to share the memories.   said HD is currently unmounted.

Sine my lastpost I installed 'Picasa' through 'Wine' sadly to no avial :( why i here you ask , picasa tends to find media you didnt know you had.

I have a few data recovery /forensic dectection tools installed , bt cannot locate them to use them.

if you need any more info please do not hesitate to ask.

I  will try the link above .

---

### Post by bumanie on 2008-03-14
Photorec is an extension to test disk which is a data/partition recovery program. I wouldn't suggest using that unless absolutely necessary as you've had so many partition changes (unless you intimately know each partition from the past). All I can say is that I have read that photorec is good (as is test disk), but I have never needed to use it myself. If photorec doesn't work, you could look up 'dd rescue' commands and try them. I plan to learn that soon, but as yet know very little. As I understand things, 'dd' will scan and try to recover every sector of a hard disk.

---

### Post by slick1a on 2008-03-14
Installed the following packages:                   
libntfs9 (1.13.1-6)
testdisk (6.6-1)
picasa (2.7.3736-11)
gddrescue (1.2-1)
photorec
afio (2.5-4)
buffer (1.19-9)
cdrecord (10:2.01.01a33-0ubuntu2)
gawk (1:3.1.5.dfsg-4ubuntu1)
helix-player (1.0.6-3)
liblzo1 (1.08-3)
lzop (1.01-4)
mindi (2.22-1ubuntu1)
mindi-busybox (1.2.1-2)
mkisofs (10:2.01.01a33-0ubuntu2)
mondo (2.22-1)
mondo-doc (2.22-1)
mozilla-helix-player (1.0.6-3)
ms-sys (2.1.0-1)
mtools (3.9.10.ds1-3)
syslinux (1:3.36-4ubuntu5)

obviously some of the above are additional requirements , but the problem i have is i do NOT know  where to find them in order to use them.

Its all well and good advising on different things to use , but if i cant locate them in applications etc , one is at a loss.

i hope this helps ??????

---

### Post by bumanie on 2008-03-14
As far as I am aware photorec and certainly test disk run off a live cd. You need to  download the iso and burn them to disk, at least that's how test disk works.

---

### Post by slick1a on 2008-03-14
thankies bumanie, 

I tried that too , an image was burned to disk , however when i installed the cd , i was told i had inputted a blank cd...grrr grrr and double grr.

The programmes are already installed on my machine , but i cannot locate them to use them .

have since found thread [http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922)

going to have a crack on that one i think.  get back to me with any more ideas as all are greatly appreciated.

---

### Post by slick1a on 2008-03-14
I got as far as
Code:

sudo apt-get install alien <here no probs ldconfig deferred processing now taking place


Code:

wget [http://www.cgsecurity.org/testdisk-6.6-1.i386.rpm](http://www.cgsecurity.org/testdisk-6.6-1.i386.rpm) < for this :

wget [http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm](http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm)
--17:01:39-- [http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm](http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm)
=> `testdisk-6.6.1.i386.rpm'
Resolving wwwcgsecurity.org... failed: Name or service not known.

Code:

sudo alien testdisk-6.6-1.i386.rpm <for this :

wget [http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm](http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm)
--17:01:39-- [http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm](http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm)
=> `testdisk-6.6.1.i386.rpm'
Resolving wwwcgsecurity.org... failed: Name or service not known.

Code:

sudo dpkg -i testdisk_6.6-2_i386.deb <and for this :

wget [http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm](http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm)
--17:01:39-- [http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm](http://wwwcgsecurity.org/testdisk-6.6.1.i386.rpm)
=> `testdisk-6.6.1.i386.rpm'
Resolving wwwcgsecurity.org... failed: Name or service not known.

By taking a quick glance @ my above thread link you will see the dilema im having.

1. what am i doing incorrectly ?

2. I have the tools i need but cannot locate them to use

3. Can anyone help ????

---

### Post by methosology on 2008-03-14
Hi all, anyone have problems with testdisk not displaying all sub-directories? I was moving my windows partition (shifting some 130GB of data, never really smart) using gparted but had to stop after an hour into it (it said 10 hours was needed). Now I have a broken windows partition that I can mount and access but with many unreadable files. Using testdisk I just want to recover some documents from my personal folders, but it only lists files in my vista partition up to those starting with M. Note I can still see all sub-directories of the ntfs drive by just navigating to VistaOS. Please any help is welcomed and I should note I'm just starting to use linux.

---

### Post by slick1a on 2008-03-15
The following is intended for research purposes only , I take no resposibility if you do not  read this post in full before trying anything.

If TestDisk is not yet installed, it can be downloaded from TestDisk Download. Extract the files from the archive including the sub-directories.

 One condition:

    * TestDisk must be executed with "Administrator privileges." 

Important points for using TestDisk:

    * To navigate in TestDisk, use the Arrow and PageUp/PageDown keys.
    * To proceed, confirm your choice(s) with the Enter key.
    * To return to a previous display or quit TestDisk, use the q (Quit) key.
    * To save modifications under TestDisk, you must confirm them with the y (Yes) and/or Enter keys, and
    * To actually write partition data to the MBR, you must choose the "Write" selection and press the Enter key. 

Code sudo testdisk-6.9/linux/testdisk_static

Here's how i did it; 

1. opened terminal typed 'pho' and hit the autocomplete button (tab) why didnt i just think of this in the first place ?? dur !!

2. Enlarged terminal window as 'Photorec' needs 25 lines to work

3. Of options : Disk /dev/hdc - 2048 B (R0)  selected Disk /dev/sdf - 320 GB / 298 GiB (R0)

4. Hit proceed   - N/B of note: Some disks won't appear unless your a root user. Disk capacity must be correctly detected for a successful recovery. if a disk listed above has an incorrect size, check jumper settings, BIOS detection, and install the latest OS patches and disk drivers.

5. now select the partion table type, pushing enter when done :
[intel] Intel/PC Partition   < my choice > usually the default value is the correct one as TestDisk auto-detects the partition table type
[Mac] Apple partition map
[None] non partitioned media
[Sun] Sun solaris partition
[Xbox] Xbox partition
[return] return to disk selection

6. checked file options photorec searches for, as i'm specifically searching for .jpegs

7. To recover lost files, Photorec needs to know the filesystem type were the files are stored:

[ EXT2/EXT3]  EXT2/EXT3 filesystem
[ Other] FAT/NTFS/HFS+/ReiserFS/. . .       < my choice

8. then i got fumbled so i looked up  

9. [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

10.  After following the above link , I located missing .jpegs . I recommend this tool for anyone who has accidently deleted a hard drive or has missing files which YOU KNOW are there somewhere.

---

