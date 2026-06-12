---
title: "Clean Install"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by AcademyKP03 on 2007-10-23
All,

I upgraded to 7.10 and after trying hours to get my system back from 7.04 - have finally concluded that I need to just do a new install to the computer.  Problem is - I can't get to the point of actually installing 7.10.  I keep getting to the BusyBox dialog ..... it was suggested that I try the Alternate CD ... which i did ... but whenever I try to run that CD - I get to the point where it is detecting hardware for CDROM and it sits there frozen at 85% complete.  I've done this a number of times, and keeps freezing at 85%.  I'm running out of ideas ..... I just want a fresh install!  Any suggestions would be appreciated.  Please note I'm completely new to using ubuntu

thanks

---

### Post by mramsey on 2007-10-23
> **AcademyKP03 said:**
> All,

I upgraded to 7.10 and after trying hours to get my system back from 7.04 - have finally concluded that I need to just do a new install to the computer.  Problem is - I can't get to the point of actually installing 7.10.  I keep getting to the BusyBox dialog ..... it was suggested that I try the Alternate CD ... which i did ... but whenever I try to run that CD - I get to the point where it is detecting hardware for CDROM and it sits there frozen at 85% complete.  I've done this a number of times, and keeps freezing at 85%.  I'm running out of ideas ..... I just want a fresh install!  Any suggestions would be appreciated.  Please note I'm completely new to using ubuntu

thanks

Use GParted and re-format the hard drive.  I believe that there is a copy of gparted on the LiveCD. Someone correct me if I am wrong.

Once reformatted you should be able to install...Hope this helps.:)

---

### Post by sugarland2k on 2007-10-23
try to check your system with a Ubuntu live CD ?  Can you data check your alternate install CD / DVD ?  it may have issues.  The 7.10 upgrade took me 2 days with my 6Mbps DSL and many (6-7) complete restarts but it finally worked.  Don't give up hope.

---

### Post by AcademyKP03 on 2007-10-23
How do I run GParted from the LiveCD? I know how to get into the bios and select the drive for the CD to boot from .... but then I would get the startup menu from the CD .. start/install, ect .... is there a section within that menu that has reformat?  I don't recall that .... or is there another way to get to Gparted?

any guidance would be appreciated .....

thanks again

---

### Post by AcademyKP03 on 2007-10-23
Just for the record - I can't get the LIVE CD to run .... if i could, then I would be able to install it ..... whenever I try to get the Live CD to start/install ... kicks me out to the BusyBox dialog box ... the same thing it was doing when I tried to upgrade from 7.04 to 7.10 and then restarted .... so seems I cant get any traction whether or not it CD LIVE or not .... so i went wit the alternate CD to see if it would help and it hasn't .... i tried to select the rescue mode .... but didn't work ... keeps getting stuck at 85% when detecting hardware - (CDROM) ....  i like the idea of completely reformatting the disk ... but how do I do that if the LIVE CD and the alternate CD can't run?

---

### Post by az on 2007-10-23
It sounds like the Gutsy kernel does not like your hardware.  Is it a very recent machine?

---

### Post by AcademyKP03 on 2007-10-23
here's my specs

HP Pavilion a520n
3200 AMD Athalon XP Processor (2.2G)
2 Gigs RAM
nvidia graphix card
PNY Verto GeForce FX AGP 5200 AGP

I did have a wireless keyboard and mouse - but I plugged both of them in order to simply things .... also I have a sound card (sound blaster LIVE) ... not sure if that would do anything ....

Any idea how to blast my computer?

---

### Post by AcademyKP03 on 2007-10-23
So I just tried to load Xubuntu CD to see what would happen ....selected start/install from menu. ... and again *surprise* got the BusyBox dialog box again....

Is there a bootable disk that will completely nuke my drive?

---

### Post by AcademyKP03 on 2007-10-23
Last note ... when I selected "check CD for defects" on Xubuntu - - got me back to the BusyBox again .....

---

### Post by mramsey on 2007-10-23
> **AcademyKP03 said:**
> Last note ... when I selected "check CD for defects" on Xubuntu - - got me back to the BusyBox again .....

Don't know if this will work... Try disableing the hard drive in the bios and then boot from the CD. It's a long shot but it might work.

---

### Post by AcademyKP03 on 2007-10-23
K, I'll try that and post my results in a few minutes ...

thanks

---

### Post by AcademyKP03 on 2007-10-23
wouldn't that be the same thing as the "order" of booting sequence?

ie have the CDROM with 7.10 Live boot up is first priority - where the harddrive selection is disabled?

---

### Post by AcademyKP03 on 2007-10-23
No luck ......

Isn't there a last resort option?  something boot disk that reformats?

---

### Post by AcademyKP03 on 2007-10-23
Not sure if this helps or not ,,,, able to run Super Grub Disk

This is what I found out:

NATURAL   LINUX    LINUX-SCSI     GRUB    HURD
1              hda        sda             (hd0)      hd0

-----

Partitions

N        IDE              SCSI             GRUB                 TYPE           0S

1        hda1              (hd0,0)          hd0s1                ext2fs          Ubunut710 \n \l
5        hda5              (hd0,4)          hd0s5                SWAP

-----

Any ideaS?

wish super grub had a reformat option!

---

### Post by maniac_X on 2007-10-23
> **AcademyKP03 said:**
> No luck ......

Isn't there a last resort option?  something boot disk that reformats?

[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php) :)

.

---

### Post by be4truth on 2007-10-23
If you have an XP or Windows98 installation CD at hand you could wipe out the Master Boot Record MBR.
Boot the XP disk, go into repair console and type FIXMBR (check with help).
After that your Ubuntu Live CD should boot fine. A Windows 98 boot floppy will do the same.
One thing that sometimes helps. Go into the BIOS and load default setings. Then Reboot into your Ubuntu Live CD.

---

### Post by AcademyKP03 on 2007-10-23
No windows CD .... thanks though....

Going to try and use the GPARTED live iso CD and see if that works ......

HOPE it does the trick ... thanks ... i'll post my results shortly

---

### Post by be4truth on 2007-10-23
The gparted Live CD will not change the MBR. You said that you can't boot into a Live CD.

---

### Post by mramsey on 2007-10-23
I've used an app called killdisk for deleting hard drives before buthave never reformatted one after doing so. Try searching Killdisk in google.

---

### Post by maniac_X on 2007-10-23
> **be4truth said:**
> The gparted Live CD will not change the MBR. You said that you can't boot into a Live CD.

actually, be4truth is correct, if you are trying to reinstall Windows MBR, GParted Live CD won't solve that for you.
But....I have a win98bootdisk CD .iso file somewhere. I'll see if I can find it and upload to rapidshare. Hopefully I find the notes 
with it as to the command to use from Win98 boot to repair the member.

EDIT: the notes I have is as follows:```
Boot from the CD. You will soon see a black background in your monitor and 
will be given three choices.

These are,  

                     1. Start computer with CD-ROM support

                     2. Start computer without CD-ROM support

                     3. View the Help file.



Choose number 2, 'Start computer without CD-ROM support'.

After a few minutes, you be at the prompt:
 A:\_



 After the     A:\_   prompt and type the command** fdisk /mbr** and wait for the command to 
work. When it is finished, press 'Ctrl'+'Alt'+'Del' to reboot, and remove the CD.

Your 'boot sector' will be pointing to Windows again.


```

[b]Here is the link for the Win98SE Boot CD: [http://www.sendmefile.com/00589878](http://www.sendmefile.com/00589878) 
Burn like you would any other .iso image and you will have a bootable Win98SE setup disk. :) 
Hope this gets your MBR issue resolved. [/b]

.

---

### Post by mramsey on 2007-10-23
> **maniac_X said:**
> actually, be4truth is correct, if you are trying to reinstall Windows MBR, GParted Live CD won't solve that for you.
But....I have a win98bootdisk CD .iso file somewhere. I'll see if I can find it and upload to rapidshare. Hopefully I find the notes with it as to the command to from Win98 boot to repait the member.

He's trying to reformat the entire drive and start fresh.

---

### Post by maniac_X on 2007-10-23
> **mramsey said:**
> He's trying to reformat the entire drive and start fresh.

hehe, guess that's what i get for skimming the thread with little sleep. :)
GParted will prob solve his reformat issue nicely then. I use it every time I do a fresh install now.

---

### Post by caedmon on 2007-10-23
Try this!  It worked for me when I had similar problems:

sudo dd if=/dev/zero of=/dev/hda bs=521 count=1

it will completely wipe your drive so be carefull!

good luck

:lolflag:

---

### Post by az on 2007-10-23
> **AcademyKP03 said:**
> 
Any idea how to blast my computer?

Boot the 7.04 cd.

What you are describing has nothing to do with your hard disk.  The cd has to load the kernel before it does anything - including the integrity check.  That kernel does not boot on your machine.  You will not be able to run Gutsy on your machine with that kernel.

---

### Post by adrian15 on 2007-10-25
> **AcademyKP03 said:**
> 
wish super grub had a reformat option!

You will have to wait some time till I decide to develop rescatux.

;)

adrian15

---

### Post by jpepin on 2008-03-18
I know it's probably way too late to help the original poster, but I had the same problem, and the resolution was quite easy...

You must have an internet connection.  

All I had to do was connect my laptop via cat-5 (couldn't configure my wireless until after install due to restricted drivers), and it finished up.  I was frozen at 85%, and it said "installed tomboy".  No need to restart the install, just hook it up and it'll figure it out.  For some reason, the install hangs up due to an inability to resolve the repository servers' addresses.  After connecting the Ethernet cable, install was done in minutes.

Here's a link to someone that also had the same issue in Xubuntu:
[http://ubuntuforums.org/showthread.php?t=605599]("http://ubuntuforums.org/showthread.php?t=605599")

Hope this helps someone!

---

