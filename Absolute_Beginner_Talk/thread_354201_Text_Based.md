---
title: "Text Based"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by TrIde2188 on 2007-02-05
Hi, I'ma fairly new linuxian :]


although ive used it before, i had help from my friend who uses it alot, hes moved away hardly speak to him now, im trying to isntall well ive tried many differnet types of distros all seem to either come up with errors, not work, dont boot up, cant boot up, etc

Im using a very old pc

AMD K6 2

500MHz

128 Ram

20GB HDD


bascially i pretty much wnat to only install via text based, and then to have a very low spec gui being used, so far ive found a few text based isntalls.. none work.


also ive only got a cd drive on the laptop, so i cant burnany dvd's to it.


Any Help/Ideas/Tips/links to iso's or other distros i could use if nothing cna be done about it wiht ubuntu would be extremely welcome :]


p.s

Yes ive googled for the past two days trying to get distros working.



EDIT: the main reson for wanting text based is, all gui installs ive tried, jsut crash on me due to the low RAM.
Although isuceededin this with mandriva it kept coming up wiht the error missing media.cfg

:]

---

### Post by lucia_engel on 2007-02-05
Here's a guide you should read. 

[Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

It maybe a little bit complicated since you're fairly new, but if you have any questions about it, I'll try to help as much as I can.

You can also try another lightweight distro called [Damn Small Linux]("http://www.damnsmalllinux.org/") if you don't want to go through the hassle above.

---

### Post by mikewhatever on 2007-02-05
As far as I know, Ubuntu with gnome is no go for a PC with 128 MB of RAM. You should try Xubuntu though. I am sure others will be along with other nice options.
Good Luck.

---

### Post by TrIde2188 on 2007-02-05
Thanks for the reply!

Ill scour through the documentation. and get back here if i have/donthave anyproblems :]


Cheers.



TrIde

---

### Post by TrIde2188 on 2007-02-05
Just downlaoded the alternate version of ubuntu, stuck it in my drive and same thing is happening which happened when i tried xubuntu, which is it failes to mount/load installer components form the cd

Grrrr


it must be ubuntu, coz its not the drive it was workinga few hours ago when i tried to isntall mandriva =S and gentoo... and fedora.... and freespire.. etc etc 


any other ideas?

---

### Post by lamego on 2007-02-05
Also you should be more clear about "text mode installers don't work" ...

---

### Post by TrIde2188 on 2007-02-05
> **lamego said:**
> Also you should be more clear about "text mode installers don't work" ...

Well They Start to iusntall and usually come up wiht errors, or as ive jsut said, dont load the cd.


On the other hand gui based installs jsut crash on me.

---

### Post by lamego on 2007-02-05
Eventually you have an hw problem or your hw is not supported by the linux kernel, if you do have such problem don't forget to write down the error message so that we can help you further,

---

### Post by RomeReactor on 2007-02-05
I've installed [Puppy Linux]("http://www.puppylinux.org/user/viewpage.php?page_id=1")  on an IBM Aptiva with a 200mhz processor, a 1GB HD and 80 MB of ram. Runs a little slow, but without hangups of any kind. Installation was flawless, with working multimedia.

---

### Post by TrIde2188 on 2007-02-05
the only error messages i get are bascially saying... that it was unable to find a cdrom to mount.


evne htough its jsut booted off of it..

---

### Post by TrIde2188 on 2007-02-05
Ill try out that puppy linux now :] cheers

---

### Post by TrIde2188 on 2007-02-05
Didnt work kept getting erros on the screen saying

hdc:media error (bad sector): status=0x51 {DriveReady SeekComplete Error }
hdc:media error (bad sector): error =0x34
end_request: I/O error, dev 16:00 (hdc), Sector 12

that then repeating but the sector number changing 


then that eneded and said

Puppy was unable to locate the file usr_cram.fs.
This file is the entire /usr folder, as a compressed read-only f.s.,
and its absence means that x cannot be started, but you well at least get the cmd prompt.


=/

then said press enteri did so it ended up saying

readlink: No such file or directory

Sorry, cannot start X. File /usr/X11R6/bin/X missing.
If X is supposed to be installed, probably Puppy was unable
to mount usr-cram.fs on /usr.

then takaes me to the command promptt...


=/

---

### Post by RomeReactor on 2007-02-05
Hmmmm... not sure about this, but either the cd's aren't being burnt properly (low speed, for example, if you have an old cdrom on the computer you're installing Ubuntu) or it's hardware failure on the cdrom (or maybe it's just dirty). My money is on the image being burnt on high speed (a lot of older hardware has trouble with that).

---

### Post by TrIde2188 on 2007-02-05
ah right ok, yea i dont really know what the differences of slow or fast cept well the speed differnece, i dont know what affect that has but ill try installing on the lower speed :]


ill get back here to update.

---

### Post by maxamillion on 2007-02-05
You might need to try installing debian sarge with the default 2.4 kernel that comes with the installation image, I've run into this problem with some older hardware before and when push comes to shove, debian sarge seemed to be the only thing that would boot on it for installation.

---

### Post by TrIde2188 on 2007-02-05
I know what kernels are roughly, but please could you go into greater detial by what you mean by Debian Sarge ETc.

Confused me up top a bit.

---

### Post by TrIde2188 on 2007-02-05
Rihgtio ive tried isntalling at a slower speed tried 2x then 4x then 8x

it stillcoms up with this error

I/O Error!

Device: [3:0:0] LITE-ON DVDRW SOHW-1693S KS06 (D:) (ATA)

ScsiStatus: 0x02
Interpretation: Check Condition

CDB: 2A 00 00 04 4F 20 00 00 20 00
Interpretation: Write (10) - Sectors: 282400 - 282431

Sense Area: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00 00 00
Interpretation: Write Error


 =/

---

### Post by TrIde2188 on 2007-02-05
Okay i burnt it at 10x..

comes wiht this error after booting

the CD-ROM does not seem to containa valid 'Realease' file, or that file could not be read corerectly.

=/ any ideas?

---

