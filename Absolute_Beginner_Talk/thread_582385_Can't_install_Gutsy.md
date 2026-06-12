---
title: "Can't install Gutsy"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by XiaoSiuMai on 2007-10-19
hey guys im having a problem with my ubuntu install. i can boot up with the cd all the way to the desktop, then when i install, it gives me an error at about the 30% range. it says:

"[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard drive. It may help to clean the CD/DVD, to burn the CD/DVD at lower speed, to clean the CD/DVD drive lens, to check whether the hard disk is old and in need of replacement, or to more the system to a cooler environment. "

i have a dell 1420 with:
Intel Core 2 Duo 2.0Ghz
2 GB RAM
128 MB dedicated video card
160 GB HD

i burned multiple cds from 2 different computers at 1x burning speed. theres one strange part, the day before i tried it and got the same message but it appears at around the mid 20 percent range but now its low 30 percent.

please help me im new to ubuntu but it looks very promising. Thanks in advanced

-Phil

---

### Post by Pumalite on 2007-10-19
Clean the lens in your burner. Try the CD's in different computer.

---

### Post by DalaiDakkar on 2007-10-19
Hi, 

I was running ubuntu 7.04 and upgraded to 2007-10-10 RC of Gusty 7.10 using update-manager. The following errors were generated
ERROR got an error from dpkg for pkg: 'gnome-themes': 'subprocess post installation script returned error exit status 127
ERROR got an error from dpkg for pkg: 'gnome-accessibility-themes': 'subprocess post installation script returned error exit status 127
ERROR got an error from dpkg for pkg: 'ubuntu-desktop': 'subprocess post installation script returned error exit status 127
ERROR SystemError from cache.commit(): installArchives() failed

Then I received an warning that the upgrade had failed and that the machine might be in an unusable state. On reboot x-starts but my screen is black except for a spinning busy mouse pointer. 

From the CLI apt-get install gnome-themes returned the error:
gtk-update-icon-cache: symbol lookup error: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol g_once_init_enter_impl

That message is repeated three times.

Help please

---

### Post by XiaoSiuMai on 2007-10-19
> **Pumalite said:**
> Clean the lens in your burner. Try the CD's in different computer.

the computer with built in the beginning of sept..so i dont think thats the issue. i ran the check cd integrity option on the live cd and it came up with 0 errors

---

### Post by Pumalite on 2007-10-19
Did you do md5sum on the iso?

---

### Post by XiaoSiuMai on 2007-10-19
sry im completely noob to this. what does that mean? 

note: i used these intstructions to install ubuntu:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by mistergq on 2007-10-19
what program did you use to burn the cd?

---

### Post by XiaoSiuMai on 2007-10-19
i used 2 programs for 2 different cds

1) Roxio Creater DE
2) InfraRecorder (open source)

---

### Post by Pumalite on 2007-10-19
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by XiaoSiuMai on 2007-10-19
i just did md5sum check on the iso and it was correctly downloaded

---

### Post by XiaoSiuMai on 2007-10-19
i had a feeling that it was my hd but then my computer is less than 2 months old

please i need more help

---

### Post by corevette on 2007-10-19
> **Pumalite said:**
> Clean the lens in your burner. Try the CD's in different computer.

I had the same problem he/she had and i just kind of wiped down the reader with a tissue and seemed to work fine after that...

---

### Post by XiaoSiuMai on 2007-10-20
ok i tried wiping the reader...no luck...same message still appears. any other ideas? thanks for all whos helping me now and who will help me...thanks alot!

---

### Post by Urbanmoth on 2007-10-20
I have the exact same problem - I have 2 CDRom drives - both burners in my machine and 3 separate hard drives (one is a SATA, the others PATA). 

I have to date:

1. downloaded the iso 4 times from 3 separate locations
2. verified the iso file each time prior to burning
3. created 6 different disks using 3 software tools (XPBurner and nero on XP and the CD\DVD burner in Gusty (live CD) using both my drive (3 times each)
4. I have verified all disks created - no errors.
5. Have attempted to install to different locations on all three hard disks.

Oh and did I mention I used different media - including one burn on a high quality TDK CD-R, just in case I had a bad batch of my standard fair.

I get the exact same issue every time on install (at about 23 -25% install) - I am starting to suspect a memory issue - memtest is my next point of call.... but if any guru out there recognizes this issue I will most happy to take any and all advice.

UM

---

### Post by Duck2006 on 2007-10-20
> **Urbanmoth said:**
> I have the exact same problem - I have 2 CDRom drives - both burners in my machine and 3 separate hard drives (one is a SATA, the others PATA). 

I have to date:

1. downloaded the iso 4 times from 3 separate locations
2. verified the iso file each time prior to burning
3. created 6 different disks using 3 software tools (XPBurner and nero on XP and the CD\DVD burner in Gusty (live CD) using both my drive (3 times each)
4. I have verified all disks created - no errors.
5. Have attempted to install to different locations on all three hard disks.

Oh and did I mention I used different media - including one burn on a high quality TDK CD-R, just in case I had a bad batch of my standard fair.

I get the exact same issue every time on install (at about 23 -25% install) - I am starting to suspect a memory issue - memtest is my next point of call.... but if any guru out there recognizes this issue I will most happy to take any and all advice.

UM

Did you burn the cd,s at X4 or higher?

---

### Post by Girya on 2007-10-20
I'm an absolute N00b Too, so take my advice with a grain or two of salt. I had a similar problem. It turned out that there was a floppy drive enabled in my bios but I had no floppy drive installed. As soon as I disabled the floppy drive in my bios I was able to install 7.10 without a problem. I had 7.04 running on the same computer with no issues so there is something that changed that causes a conflict. I found it when I was rooting around in the hardware manager and saw a entry for a floppy drive. My computer is like yours in that it is only a couple of weeks old.  Kevin

---

### Post by Urbanmoth on 2007-10-20
> **Duck2006 said:**
> Did you burn the cd,s at X4 or higher?

For the first couple, no - full 52X but I did do 1 at 1x (and that takes some time!)  and the other 3 at 16X

UM

---

### Post by k3lt01 on 2007-10-20
I had a similar problem with Feisty a few weeks ago. Windows was the problem as if it is on the HDD and you start the machine it goes into memory. I had to do a total reformat on my machine (used RedHat, long story) wiped out windows (RedHat didn't work either) and installed Feisty no problems.

---

### Post by Duck2006 on 2007-10-20
You can all try with a  text-based install CD.

---

### Post by Urbanmoth on 2007-10-20
> **Girya said:**
> I'm an absolute N00b Too, so take my advice with a grain or two of salt. I had a similar problem. It turned out that there was a floppy drive enabled in my bios but I had no floppy drive installed. As soon as I disabled the floppy drive in my bios I was able to install 7.10 without a problem. I had 7.04 running on the same computer with no issues so there is something that changed that causes a conflict. I found it when I was rooting around in the hardware manager and saw a entry for a floppy drive. My computer is like yours in that it is only a couple of weeks old.  Kevin

Had high hopes for this - my system is indeed floppydiskless and lo, the BIOS had a floppy configured - but no joy - disabled the floppy but no improvement. Nice idea, however, thanks.

UM

---

### Post by XiaoSiuMai on 2007-10-20
thanks for all the feedback so far...i tried all methods posted but no luck yet either..the whole point of doing this was that i wanted to dualboot so complete wipe isnt a option...thanks for that idea tho ill use it was a last resort...any more ideas guys?

---

### Post by Mayfairy on 2007-10-20
I was upgrading my Feisty to Gutsy through a graphical interface. It had already downloaded everything and installation was at about 70-80% when I received some error messages and installation was aborted. 
I checked my '/var/log/dist-upgrade/main.log' and at the end of the file was this:

2007-10-21 05:11:04,653 ERROR SystemError from cache.commit(): installArchives() failed
2007-10-21 05:12:10,558 DEBUG setting MinAge to 2
2007-10-21 05:12:10,558 DEBUG no file '/etc/apt/apt.conf.d/25adept-archive-limits'

Any ideas how to finish my upgrade? Right now I'm doing 'apt-get upgrade' and next going to do dist-upgrade through a shell.

EDIT: 
Did apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get install -f
cat /etc/lsb-release

No errors and cat identified my system running Gutsy Gibbon. 

Successful upgrade in the end. :)

---

### Post by XiaoSiuMai on 2007-10-21
please help us...we need help badly!

---

### Post by Urbanmoth on 2007-10-21
> **Duck2006 said:**
> You can all try with a  text-based install CD.

OK, this works for me, now working nicely on 7.10 no problems - damm this OS is good - even if I have had a nightmare getting it to install - it is worth it. Only reason I am keeping XP is for some very complex word \ Excel stuff I do - just waiting for OpenOffice to add a couple of extra features, that I am sure are on the cards, and it's goodbye Microsoft for good :)

XiaoSiuMai, Have you tried the text based install? It is not as scary as it sounds.

---

### Post by XiaoSiuMai on 2007-10-21
ill be trying that now...ill give u my results when im done...wish me luck!

---

### Post by XiaoSiuMai on 2007-10-22
ok i installed most of it successfully...it failed on the installing software part..but core system was  installed...

my problem now is that when it boots into ubuntu its all text..then keeps booting all check hardware etc...then asks for username and pass...after that its still text and in a command prompt type thing..

what do i need to do to boot into the "actual" ubuntu desktop?

(NOTE: Im still linux noob)

---

### Post by pbrockway2 on 2007-10-22
> ok i installed most of it successfully...

Was that using the text based install?  I ask because I'm having the same problem - io error using multiple downloads, multiple media, on two different laptops.

I'm trying another machine to burn my CD now in case that was the problem.  And mostly posting this so you know you're not alone!

---

### Post by XiaoSiuMai on 2007-10-22
yea this was with the alternate iso (text) install....im just simply stuck outside and i have no idea how to boot into the desktop

---

### Post by pbrockway2 on 2007-10-22
I can't really advise you - but if the desktop software hasn't been loaded, then you won't be able to I guess.

My feeling is that it would be better to have a clean installation with no problems, rather than patch up something that wasn't right.

In my case, the villian was the CD burner.  I was using a Windows machine and  InfraRecorder (similar to you I guess).  I subsequently checked the hashcode of the file I downloaded and it was correct.  However when I chose the CD option of checking the disk integrity it found an error in one file.

I have just used another machine (a linux one) and burnt disk number three v-e-r-y s-l-o-w-l-y using k3b.  And it has sucessfully loaded onto the first (newer) of two laptops.  I'll know about the other one in the morning - it's 1:30am here and I can't be bothered waiting for it to finish.

If you haven't done so, you should try another CD burner.  Good luck!

---

### Post by XiaoSiuMai on 2007-10-23
i alrady tried 2 different burners

---

### Post by XiaoSiuMai on 2007-10-25
still no progess...all cds are fine...burned with different burners at low speed...live cd fails at 30ish percent and text install installs core system but fails at install software at 6%

can anyone think of solutions?

---

