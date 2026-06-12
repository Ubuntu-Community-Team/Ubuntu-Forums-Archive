---
title: "no boot live cd"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by ricwed on 2007-10-18
Hi all
I am trying to install linux on a blank harddrive on an older pc. I had ubuntu 6.0.6 running on it with windows xp and then it would not boot any longer after it froze up and I hit the power button. I cleared off the harddrive with dban. I have changed the boot sequence in the bios to boot from cd first but all I get is a message: Disk boot failure, Insert system disk and press enter. Is there something I need to do to prepare the blank drive first?  I have lost my windows 98 disk. I have tried the alternate ubuntu cd and pclinuxos-2oo7.iso.  Nothing will boot. Any help would be greatly appreciated.

---

### Post by Pumalite on 2007-10-18
256 MB RAM or less> Xubuntu Alternate CD. Post specs.

---

### Post by ricwed on 2007-10-18
256 MB RAM . I tried the kubuntu alternate cd, ubuntu edgy eft, and ubuntu 6.06. Nothing boots except dban and acronis tools. It is an azus mb with amd processor .

---

### Post by ricwed on 2007-10-18
It is a seagate 40 gb harddrive. Do you need any more specs?

---

### Post by Pumalite on 2007-10-18
Kubuntu is too heavy for your system if you want it fast. Xubuntu has a lighter Desktop and is a better option for you.

---

### Post by ricwed on 2007-10-18
You are right. I had it installed and it was slow.  My problem is I cant get any live cd to boot.

---

### Post by Pumalite on 2007-10-18
You have to use Alternate CD.

---

### Post by ricwed on 2007-10-18
I tried that also.  I'm thinking i have to have a windows os installed first before I can install a linux os?  I have lost my windows xp and 98 installation disk so I hope not.

---

### Post by Pumalite on 2007-10-18
You can have a 'solo' Ubuntu. Make sure your hard drive is formatted and recognized by your BIOS.

---

### Post by Fixman on 2007-10-18
I know this spinds stupid, but...can you boot normally your PC?
Do you have a floppy inside the case?

---

### Post by ricwed on 2007-10-19
I have partitioned the hard drive and formatted and now it boots to C:\>     What command do I use to boot the live cd, or is this possible?

---

### Post by spur on 2007-10-19
Check your bios is set to boot from the cd first. Usually you press the 'delete' button when the computer is starting is starting up. Have the cd in the drive when you boot.

---

### Post by ricwed on 2007-10-20
> You can have a 'solo' Ubuntu. Make sure your hard drive is formatted and recognized by your BIOS.

The way I partitioned and formatted the drive was with a windoze 98 iso  which I downloaded and booted from my cd drive. I dont have a floppy drive but I guess I can get one. Now I have a C:\>.  I still can't boot to a live linux cd.

---

### Post by OldTimeTech on 2007-10-20
First and foremost are you using a cd that you have burned with Ubuntu/Xubuntu on it....did you burn that at the slowest speed like 4x, 8x or so.  Did you check to make sure the cd was verified.

Secondly, if your using a burned cd it has gparted on and that's what needs to be used to set up your hard drive, not with a windows disk.

I would say you have either a bad burned cd or you cd is dirty and needs cleaned.

---

### Post by ricwed on 2007-10-20
> First and foremost are you using a cd that you have burned with Ubuntu/Xubuntu on it....did you burn that at the slowest speed like 4x, 8x or so. Did you check to make sure the cd was verified.

Secondly, if your using a burned cd it has gparted on and that's what needs to be used to set up your hard drive, not with a windows disk.

I would say you have either a bad burned cd or you cd is dirty and needs cleaned.

Yes the disks that I burned have been verified and they work in my laptop. I just cant boot linux live cds. The cd rom reads the win 98 iso, it read dban iso, and it reads acronis so I guess it's not the cd drive.

---

### Post by Pumalite on 2007-10-20
256 MB RAM or less> Xubuntu Alternate CD

---

### Post by ricwed on 2007-10-20
> 256 MB RAM or less> Xubuntu Alternate CD

Tried that also

---

### Post by OldTimeTech on 2007-10-20
I just read in community cafe that there are a number of people that are having this same or similiar kinds of problems....one of the moderators said there might be a glitch in the installer.

My suggestion would be to wait another week and let the developers work on this.

---

### Post by Duck2006 on 2007-10-20
> **OldTimeTech said:**
> I just read in community cafe that there are a number of people that are having this same or similiar kinds of problems....one of the moderators said there might be a glitch in the installer.

My suggestion would be to wait another week and let the developers work on this.

Yes and then when you partition the drive use gparted

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Pumalite on 2007-10-20
Yeah...that also:
[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by Duck2006 on 2007-10-20
> **Pumalite said:**
> Yeah...that also:
[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

Thats very good oil there.

---

### Post by OldTimeTech on 2007-10-20
+2 Pumalite

---

### Post by ricwed on 2007-10-21
Pumalite, thanks for the link.  That is good information.  I read that Diskdrake , the default Mandrake partitioner is far superior to gparted.  I think I'll try it.

---

### Post by ricwed on 2007-10-22
I finally got xubuntu installed, after running the gparted live cd. Thanks for all your help and suggestions

---

