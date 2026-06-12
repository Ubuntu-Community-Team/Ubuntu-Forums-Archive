---
title: "DVD±RW fails to read CD-R"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by lduplantie on 2007-10-31
I recently installed Ubuntu 7.10 and noticed that my Pioneer DVR-112D DVD±RW cannot read (or even mount) CD-ROMs (pre-recorded or burnt under Windows XP). I know the drive is capable of reading or recording CDs.

Here is the output of cdrecord -scanbus:

Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
Linux sg driver version: 3.5.34
Using libscg version 'schily-0.9'.
scsibus0:
0,0,0 0) 'ATA ' 'IC35L020AVER07-0' 'ER2O' Disk
0,1,0 1) *
0,2,0 2) *
0,3,0 3) *
0,4,0 4) *
0,5,0 5) *
0,6,0 6) *
0,7,0 7) *
scsibus1:
1,0,0 100) 'SAMSUNG ' 'CD-ROM SC-148C ' 'B100' Removable CD-ROM
1,1,0 101) 'PIONEER ' 'DVD-RW DVR-112D' '1.09' Removable CD-ROM
1,2,0 102) *
1,3,0 103) *
1,4,0 104) *
1,5,0 105) *
1,6,0 106) *
1,7,0 107) *

Output of: cdrecord dev=1,1,0 -checkdrive
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
scsidev: '1,1,0'
scsibus: 1 target: 1 lun: 0
Linux sg driver version: 3.5.34
Using libscg version 'schily-0.9'.
Device type : Removable CD-ROM
Version : 5
Response Format: 2
Capabilities :
Vendor_info : 'PIONEER '
Identifikation : 'DVD-RW DVR-112D'
Revision : '1.09'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Using generic SCSI-3/mmc CD-R/CD-RW driver (mmc_cdr).
Driver flags : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R LAYER_JUMP

The command eject /dev/scd1 (-t) will open (close) the DVD tray
The command eject /dev/scd0 (-t) will open (close) the CD-R tray

I can mount a data dvd in the dvd drive, but cannot mount a CD-R.
I can mount the CD-R, tried in the DVD drive, in the CD-ROM drive.

Can you please help making the DVD drive read CD-ROM or record CDs

---

### Post by steve_b on 2007-11-01
Hope you don't mind me jumping on your thread, but I'm having almost the same issue. I posted my issue in the Multimedia section, but have yet to get a response:

[http://ubuntuforums.org/showthread.php?t=597819](http://ubuntuforums.org/showthread.php?t=597819)

Bottom line: Accessing DVDs from this drive is not a problem at all. Accessing/burning CD data/Audio CD music is just not happening.

Sounds like we are not the only folks who are having similar mount problems. Maybe we can keep this thread alive and ask others with similar issues to add their own details???

My DVD drive is an external USB drive, but like you said I know it should work reading CD-Rs and regular Audio CDs because it has done the same under PCLinuxOS 2007 and OpenSUSE. I am using it with another PC though, so maybe that is really the issue.

Any expert opinions would be truly appreciated. I'm really liking Ubuntu, but if I can't burn/play CDs, then it is back to PCLOS for me. Most everything else works great, but this one is more than just a bit puzzling and frustrating.

---

### Post by Pumalite on 2007-11-01
Does k3b recognize your burners?

---

### Post by steve_b on 2007-11-01
> **Pumalite said:**
> Does k3b recognize your burners?

For my HP dvd 940, yes. I'm actually able to rip Audio CD track s from CD as flac/ogg using k3b with no problem. k3b sees all the tracks on the CD perfectly. However, Audio CD apps like Amarok & xfmedia do not recognize the same CDs as legitimate Audio CDs.

Upon inserting an Audio CD, Amarok launches (just like I want it too for Audio CDs), but it doesn't start the CD. After selecting Engage --> Play Audio CD, I get "Could Not Read AudioCD". xfmedia doesn't respond at all after Add --> Other --> CD.

I'm thinking fstab is missing an entry somehow, but I'm not sure what to put in there in order to fix. It's as if the device is recognized as a DVD drive, but not a CD drive as one would expect when a CD is inserted.

Edit:

I did run a test of this same DVD burner/PC combination using a PCLinuxOS 2007 Live Disk and was able to play Audio CDs with no problem. So I think that proves there is no hardware issue with my particular setup. I'll use this Live disk to perform some more testing and report back.

---

### Post by lduplantie on 2007-11-01
Steve_b, No problem please let me know if you ever get your issue resolved. I agree, its hard to get replies on hardware topics.

Pumalite: Ok I learned something new. I can install KDE applications in Ubuntu/Gnome.

Yes the CD-ROM and the DVD±RW are recognized in k3b. Under Settings, all the DVD's read/write capabilities are correctly listed. When I inserted a CD-ROM in the DVD, as expected the media was not mounted. I inserted the CD-Rom in the CD-drive and a data DVD in the DVD drive, both media were recognized by k3b. I don't know if this is a problem with k3b, but when I click on the drive icon in the top left pane, an error message box appears with: Malformed URL media://dev/scd1 (or scd0 with the other drive).

Thank you all

---

### Post by lduplantie on 2007-11-07
Well after days of trying to get this dvd drive to read cd-roms in my Ubuntu PC, I decided to install the drive in a Windows PC. The same problem exist under that OS. I upgraded the F/W. No change.

Conclusion: I dumped the DVD±RW drive

I will buy a new one (not a pioneer this time around) and if it runs ok I will show this thread as resolved.

Thank you to all contributors

Update: Bought and installed LG GSA-H54N DVD±RW. Problem is solved. 

Laurent

---

