---
title: "Linux Help and questions please help"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Simple512 on 2007-10-06
Firstly im hoping this is correct section for this type of topic. If not can a moderator movie to the correct section. All help and comments are appreciated.



Ok so i downloaded ubuntu 7.04 desktop amd64 (desktop version image file) I burned it to a CD and it booted from it through bios and it loaded the OS and i launched it. It worked and was running and such.

This is what i would like to do :


 I have an internal 80 gig HD with windows currently on it. I also have a 250 gig external HD. I dont have any partitions on my internal because it wont let me. I right click the drive, clicked format and it tells me that there are programs using the drive and wont let me. Any suggestions on how to format it so that it would let me wipe it completely, then i would pop in my dell windows xp disc. Install windows and partition it in half equally. Then i would restart put in my Disc with Ubuntu on it and install that on the other partition. And spend hours installing the drivers and such.

heres my questions.

1) Stuff i install on windows such as Aim, visual basic or whatever .. will that be able to be launched if Ubuntu is running or do i have to install it twice ?

2) Does visual basic 2005 edition even work on Ubuntu or do i have to download a linux version ?

3) How do i adjust my resolution settings in Ubuntu, when i booted from disc i didnt find any options except for desktop effects which required me to install a driver for my Nvidea card which didnt work after it required a restart. ... ?

4) I have a Nvidea 7600GT - GPU
Intel Pentium D 3.2Ghz with dual core turned on - CPU
1 Gig Ram
XF-I Sound blaster audio card

Will any of these specs cause problems for Linux Ubuntu ?

5) How do i Format my C drive Huh A program that will do it? since it doesnt work in the way i explained earlier, can i do it in my setup before it loads windows ? Please be very descriptive im new to all of this.

I have many questions i just cant seem to remember them until they occur when im actually running Ubuntu. If you could help me out and give me suggestions as well to things i should do and not do with installing Ubuntu. And if you could, add me to AIM for quicker chatting and guidance it would be greatly appreciated.

My Screen name is =       simpl3 512 , thanks guys hopefully you guys can help :)

---

### Post by Pumalite on 2007-10-06
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Daveth on 2007-10-06
Hi. Welcome to the ubuntu Forum. 

Looks like you ran the live cd, but you will have problems with that nice shiny XF-I Sound blaster audio card. There is an experimental beta driver out and one of the Forum staff is going to buy the card soon, so we might get some progress. Many people have held off buying one- me included- because of this lack of driver support. Rest of your spec list is fine. The standard linux generic kernel will recognise and use both your cpu cores.

In no particular order- well, as Ubuntu and Windows will be living on completly separate partitions, and are designed differently, then you will have to load up things twice. Of course, you may find some really nice Linux programs that do not have a windows counterpart, and some Windows one with no linux version, but these is always WINE which does allow some windows progs to run in linux (not to mention the whole virtualisation thing).

No idea about VB.

Screen resolution lives in System/Preferences/ Screen Resolution.
For disk partitioing you can use Gparted, running it from the livecd- have a look at 
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

first off . You might want to have a look through

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows?action=show&redirect=SwitchingFromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows?action=show&redirect=SwitchingFromWindows)

this as well- full of useful pointers, with this

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

being everything (alomst) about dual booting windows and Ubuntu on your hard drive.

---

### Post by Simple512 on 2007-10-06
First off, wow daveth thanks for such great input to my questions and it is appreciated. I looked at the Gparted link and i see how that is useful but i have alot of stuff that i would just like to get wiped off my hard drive. So if there was another program or way to do this i would also appreciate that as well. Thank you

---

### Post by lintoon on 2007-10-06
To create 2 partitions boot off your Windows XP cd and delete your Windows partition (Follow the instructions).  You will get a blue screen with lots of text and a list of your existing partitions.  After you press "L" to delete the partition you will be taken back to the previous screen with the partition list.  At this point you will have unpartitioned space where you can specify the size you want to create.  Just create half the size of your disk and continue with the XP installation.  When you have finished installing XP, boot from your Ubuntu CD and install onto the other part of the disk.

Make sure you have a back up of your data and drivers for XP.  Especially drivers for your network card or usb (depending how you connect to the net).  This is because if you don't have driver disks for your other hardware at least you will be able to get on the net and download them.  

It's easier than it sounds.

---

### Post by Simple512 on 2007-10-06
ty lintoon , theres one question that arised from what you said. I have a dell windows xp disc. I bought a dell and they gave me the disc (obviously) will this dell disc affect anything you said. I think it is a bit different from a regular standard xp disc ..

---

### Post by Daveth on 2007-10-06
you will actually need to make a few more partitions as you will need a linux swap partition, and you really should have a separate /home partition. This is where all your files, music, pictures, love letters and rants will live, separate from the operational guts of the OS. It does mean that your can easily upgrade versions, just pointing your new version at your /home partition which it will then use quite happily.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

gives the detail. If you are nuking the partitions as Lintoon suggests then the formatting will trask all that you do not want (and all that do as well) - so be careful about your backup strategy BEFOREHAND!

---

### Post by Daveth on 2007-10-06
um- you might want to check that that XP disk is more than just an OEM restore job i.e. does actually boot and does actually hold the full XP OS. True it will allow you to restore a broken XP install but it might not let you put it back afresh......

---

### Post by Simple512 on 2007-10-06
Question about the ext3 filesystem partition .. how will windows know to make this partition in the options of whether to make it a NTFS or FAT32 Partition .. i dont remm seeing ext3 filesystem on there the last time i tried. Is it ok if i make two 40 gig partitions - NTFS and then the 1 gig swap partition NTFS also .. and it would all work out ? 
Also i have an external HD that i will keep all my personal files on during this OS crazy installing is taking place. So as it stands when i boot from my windows XP disc


and choose to partition the drive i should make the following partions

40GB - Windows partition - NTFS
40GB - Ubuntu partition - NTFS
1GB - Swap partition - NTFS (Not sure what to do with this partition ... do i do anything special when installing linux with it or just leave it be .... and why is it called swap ?)

---

### Post by Daveth on 2007-10-06
"Linux uses swap space as "extra" memory for pages of application
memory that are not being actively used by the application but have
been modified (written to).  The swap space size plus RAM size is the
total amount of virtual memory for the system.  When most of the system's
real memory is in use, and there is a need for more, some data will be
moved into swap to free real RAM memory for use by applications or for
kernel use, such as for driver buffers, files, or network packets.
This is called swapping out.  When the data that is in swap space needs
to be used it is swapped back in from swap space.  The rate at which data
is swapped to and from one or more swap spaces can be monitored with the
'vmstat' command's swap-in (si) and swap-out (so) columns."
from
[http://www.xenotime.net/linux/doc/swap-mini-howto.txt](http://www.xenotime.net/linux/doc/swap-mini-howto.txt)

I would still suggest that you make a /home partition to start with, as it is just easier than doing it after (not that that is particularly hard). If you use Gparted on your live Ubuntu cd, you can shrink the XP partition, and make the others for swap, /home, and the main ubuntu one with little effort. The Gparted guide and the [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) will guide you through. Not sure where you live but is is midnight and bedtime here. So, be well rested before you attempt this and read up well- easy if you get off on the right foot:)

---

### Post by Simple512 on 2007-10-06
ok i understand what your saying daveth but heres my situation. I messed up and installed xp over xp awhile ago and have a bunch of old accounts that just take up space. In order of what i will do first ...

1. Wipe 80gig Drive clean
2. Boot from XP disc and partition what i state earlier and install windows on one partition
3. I will then put in the Ubuntu disc and install that OS on the other partition. 
4. I will run XP install all the necessary drivers and programs that i used to have
5. I will run Ubuntu and install the necessary GFX drivers and some programs you guys recommended. 

Will all this work .. and i still need a program that will wipe the drive clean. Exactly what im saying is i download a program that will format the drive and then since nothing is on it. I will restart and boot with xp disc .. starting with 1. - 5. 


Also when i make the 1GB swap partition i make it NTFS and just leave it be correct. Can someone confirm this ^ thanks guys you are very helpful with this

---

### Post by lintoon on 2007-10-06
Ah problem.  If you have a dell cd the chances are it is a recovery cd.  Eg you put it in the drive and it simply recovers your hard drive to its original state.

If this is the case you have to resize your XP partition after you use the recovery cd.  A bootable cd like UBCD or Knoppix will have the utilties you need to resize the partition.  I can't remeber whether the Ubuntu cd allows you to do this because it's been a long time since I installed.  Someone else here may be able to confirm this.

Ideally you should create the partitions before installing any operating system rather than resizing after installing but the Dell cd may just revert the drive back to 1 partition.  Again, I'm not 100% sure on this so it may be a matter of trial and error.  

Either way UBCD or Knoppix are handy discs to have lying around.

---

### Post by Pumalite on 2007-10-06
I thing Gparted is better for this:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
(the stand alone, burn to CD, boot from, program)

---

