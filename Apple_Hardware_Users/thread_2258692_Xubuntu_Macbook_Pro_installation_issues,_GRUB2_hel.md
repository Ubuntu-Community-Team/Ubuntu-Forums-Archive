---
title: "Xubuntu Macbook Pro installation issues, GRUB2 help"
date: 2014-12-29
forum: Apple Hardware Users
---

### Post by jark_99 on 2014-12-29
Hey guys first time poster! I'm running into a issue installing Xubuntu on Mac.
I installed REFIND, booted off a usb with Xubuntu on it.

It loads up fine, i allocated 50GB to Xubuntu. Take all space and format it to EXT3 SDB4.
Set Bootloader to install to SDB4.

Everything installs, but as soon as it installs GRUB2 is says "cannot install on Target." 
I've tried multiple times and it just won't work. Is there anyway around this?

I was thinking of using 50GB of free space, and create space (100MB for EFI BOOT, install bootloader there) and install Xubuntu onto SDB4(previously mentioned). Would that still work and not corrupt my MAC filesystem? 

thanks for any help in the matter.

---

### Post by Xandoi on 2014-12-29
It shouldn't corrupt it but I would be careful

---

### Post by este.el.paz on 2014-12-30
@jark:

I don't think making the folder "EFI" is a good idea, because rEFInd makes a similar file for what it does.  You aren't mentioning which version of Xu you are installing, but these days formatting is for ext4 for the "/" disk . . . .

First thing, did you check the md5sum number of the iso?  If it doesn't match, try another download . . . that can cause problems.  I have had similar issues with installing on my MBPro, where GRUB "fails to install" when I was using the "automatic" install or "install into largest free space" . . . when setting the 50 GBs as "free space" and letting the installer run the install . . . which is the easiest.

If that doesn't work then choose "manual" . . . format and flag "/" as one partition, swap as 1 - 2x your RAM as another partition labeled as "swap," and about 10 MB labeled as "bios_grub" . . . then the install seems to go through, although possibly that partition is not actually used for GRUB . . . everything works . . . .

e.e.p.

---

### Post by jark_99 on 2014-12-30
> **este.el.paz said:**
> @jark:

I don't think making the folder "EFI" is a good idea, because rEFInd makes a similar file for what it does.  You aren't mentioning which version of Xu you are installing, but these days formatting is for ext4 for the "/" disk . . . .

First thing, did you check the md5sum number of the iso?  If it doesn't match, try another download . . . that can cause problems.  I have had similar issues with installing on my MBPro, where GRUB "fails to install" when I was using the "automatic" install or "install into largest free space" . . . when setting the 50 GBs as "free space" and letting the installer run the install . . . which is the easiest.

If that doesn't work then choose "manual" . . . format and flag "/" as one partition, swap as 1 - 2x your RAM as another partition labeled as "swap," and about 10 MB labeled as "bios_grub" . . . then the install seems to go through, although possibly that partition is not actually used for GRUB . . . everything works . . . .

e.e.p.
i've tried installing Xubuntu similar to the way you mentioned in the 2nd part of your post. confused on how to make a "bios_grub" portion. Am i just creating a regular partition for linux? and then using some extra free space to create a grub install area?
such as below:
SDA - MAC HD
SDA2 - Windows 7 Bootcamp
SDB5 - Linux install area
SDB6 - grub install area?

Will that cause any problems  with MAC? since I'm partitioning part of the free space for a boot loader? or should I just be installing the boot loader onto SDA? (650GB) primary drive?..

---

### Post by este.el.paz on 2014-12-30
> **jark_99 said:**
> i've tried installing Xubuntu similar to the way you mentioned in the 2nd part of your post. confused on how to make a "bios_grub" portion. Am i just creating a regular partition for linux? and then using some extra free space to create a grub install area?
such as below:
SDA - MAC HD
SDA2 - Windows 7 Bootcamp
SDB5 - Linux install area
SDB6 - grub install area?

Will that cause any problems  with MAC? since I'm partitioning part of the free space for a boot loader? or should I just be installing the boot loader onto SDA? (650GB) primary drive?..

@jark:

I'll try to answer your question, but first mentioning that when I first did a "dual boot" set up I used Bootcamp, but when I tried to add a "triple boot" (what you are doing) I found that BC had "locked the HD" . . . and I had to wipe the whole HD and start fresh, just using Disk Utility to create 3 large(er) partitions out of my 250GB HD . . . just mentioning that because it might be "interfering" with your install as well??  "Maybe" . . . ????

OK, second question/answer -- more or less correct in terms of what you have shown, but, why are you switching from "sda" to "sdb" for the linux partitions???  These days you can still use "primary" for partition formatting . . . .  So, moving FW, you could set up your linux partitions from the installer's GParted app, but until you know the ID and areas for Mac on the drive, I usually first use OSX DU to cut out the 50GB that I will use for the linux install . . . and set it as "free space" or if not available, set it as "FAT32" . . . .

Now, boot your install media . . . run through the initial windows until it gives you the choice of "automatic" . . . and if that has failed, then select "manual" . . . the Gparted window will open and it should show you you existing partitons for Mac & windows . . . when you 2x click on the "free space" line in the window a window will open and that will show you a line with the space in MB's . . . so usually I put the "grub" partition first . . . 10 MB . . . somwhere in that window will be the drop down menu to "flag" the partiton and choose "bios_grub" or something like that, next would be the "/" and for simplicity I just combine "home" with that, but some people make a separate "home" if they are running multiple linux OS, so they share the "home" . . . so that would be the size that will remain after you figure the "swap" . . . formatted as "ext4" and ****flagged*** as "/" . . . and finally "swap" . . . labeled as "swap."  

Sometimes I've had to toggle back and forth in the installer, like if DU isn't setting "free space" . . . you can run up thru the installer to GParted, then format your zone in GParted as "free space" then run back to the decision to install "using largest free space" and let the nstaller make the decisions . . . see if that works . . . and if it doesn't then, use "manual" as I've described above.  After install, shut the computer down . . . then do cold boot, rEFInd should open and let u choose yr system, if not, try booting with option key, etc.

GParted should show something like:  
SDA1 - MAC HD
SDA2 - Windows 7 Bootcamp
SDA3 - grub install area?
SDA4 - "/" home install area
SDA5 - swap area

But actually OSX has a few areas in front of it, so those SDA numbers might not be exact . . . enjoy the process, and, keep in mind that any time you upgrade OSX or windows they will "trash" the rEFInd "blessing" . . . so you have to read rodbooks instructions on "reblessing" rEFInd.

e.e.p.

---

### Post by jark_99 on 2014-12-30
> **este.el.paz said:**
> @jark:

I'll try to answer your question, but first mentioning that when I first did a "dual boot" set up I used Bootcamp, but when I tried to add a "triple boot" (what you are doing) I found that BC had "locked the HD" . . . and I had to wipe the whole HD and start fresh, just using Disk Utility to create 3 large(er) partitions out of my 250GB HD . . . just mentioning that because it might be "interfering" with your install as well??  "Maybe" . . . ????

OK, second question/answer -- more or less correct in terms of what you have shown, but, why are you switching from "sda" to "sdb" for the linux partitions???  These days you can still use "primary" for partition formatting . . . .  So, moving FW, you could set up your linux partitions from the installer's GParted app, but until you know the ID and areas for Mac on the drive, I usually first use OSX DU to cut out the 50GB that I will use for the linux install . . . and set it as "free space" or if not available, set it as "FAT32" . . . .

Now, boot your install media . . . run through the initial windows until it gives you the choice of "automatic" . . . and if that has failed, then select "manual" . . . the Gparted window will open and it should show you you existing partitons for Mac & windows . . . when you 2x click on the "free space" line in the window a window will open and that will show you a line with the space in MB's . . . so usually I put the "grub" partition first . . . 10 MB . . . somwhere in that window will be the drop down menu to "flag" the partiton and choose "bios_grub" or something like that, next would be the "/" and for simplicity I just combine "home" with that, but some people make a separate "home" if they are running multiple linux OS, so they share the "home" . . . so that would be the size that will remain after you figure the "swap" . . . formatted as "ext4" and ****flagged*** as "/" . . . and finally "swap" . . . labeled as "swap."  

Sometimes I've had to toggle back and forth in the installer, like if DU isn't setting "free space" . . . you can run up thru the installer to GParted, then format your zone in GParted as "free space" then run back to the decision to install "using largest free space" and let the nstaller make the decisions . . . see if that works . . . and if it doesn't then, use "manual" as I've described above.  After install, shut the computer down . . . then do cold boot, rEFInd should open and let u choose yr system, if not, try booting with option key, etc.

GParted should show something like:  
SDA1 - MAC HD
SDA2 - Windows 7 Bootcamp
SDA3 - grub install area?
SDA4 - "/" home install area
SDA5 - swap area

But actually OSX has a few areas in front of it, so those SDA numbers might not be exact . . . enjoy the process, and, keep in mind that any time you upgrade OSX or windows they will "trash" the rEFInd "blessing" . . . so you have to read rodbooks instructions on "reblessing" rEFInd.

e.e.p.

@este.el.paz

I tried again with a "/boot" made and "'/" to see if it would install GRUB2, but it still failed. I have a feeling your right about bootcamp locking up the HD on my MAC. I might just erase my Windows & Bootcamp, re-download bootcamp, create bootcamp partition and install Xubuntu & Bootloader onto that. Than afterwards, create a 3rd partition to reinstall Windows 7. In theory....this should work correct? sounds possible.

---

### Post by este.el.paz on 2014-12-30
> **jark_99 said:**
> @este.el.paz

I tried again with a "/boot" made and "'/" to see if it would install GRUB2, but it still failed. I have a feeling your right about bootcamp locking up the HD on my MAC. I might just erase my Windows & Bootcamp, re-download bootcamp, create bootcamp partition and install Xubuntu & Bootloader onto that. Than afterwards, create a 3rd partition to reinstall Windows 7. In theory....this should work correct? sounds possible.

I don't see tht you set up a labeled "bios_grub" partition . . . that would or could be the key point as far as installing GRUB goes.  Can't remember if you tried to boot your system or not, ***possibly*** you could check GParted and see if it shows if any of your linux partitions have data installed . . . if not, then the whole install is failing, not just GRUB . . . .

Anyway, the beginning in linux requires some patience . . . you could try to erase windows, but, if BC is involved I don't think you can.  Once you set, or once I set 2 partitions in BC that was it, no further partitions or anything could be done in DU.

The ****easiest**** way to have multiple systems is to use Virtualbox, or Parallels, or VMFusionware . . . installed in OSX, and then learn how to install/add iso's there and boot the various OS's that way . . . ***while in OSX***  . . . no worries about getting fan control set up with a separate linux install . . . it's all covered by OSX . . . probably much simpler . . . probably would not have to mess with BC or windows.

But, if you are a masochist like me, you would probably have to wipe the whole HD, either from install DVD, recovery disk, or ext FW HD back up . . . then reinstall OSX, reinstall rEFInd; then decide if you wanted to use BC (I didn't, which may mean some OSX features are lost, camera??) set up the extra two partitions, one for windows, one for linux; re-install windows; then try for the 3 partition linux install . . . and then read thru the Mactel FAQ at the top of this sub-forum and figure out whether the heat issues are affecting you and get that set up . . . .

e.

---

### Post by jark_99 on 2014-12-30
> **este.el.paz said:**
> I don't see tht you set up a labeled "bios_grub" partition . . . that would or could be the key point as far as installing GRUB goes.  Can't remember if you tried to boot your system or not, ***possibly*** you could check GParted and see if it shows if any of your linux partitions have data installed . . . if not, then the whole install is failing, not just GRUB . . . .

Anyway, the beginning in linux requires some patience . . . you could try to erase windows, but, if BC is involved I don't think you can.  Once you set, or once I set 2 partitions in BC that was it, no further partitions or anything could be done in DU.

The ****easiest**** way to have multiple systems is to use Virtualbox, or Parallels, or VMFusionware . . . installed in OSX, and then learn how to install/add iso's there and boot the various OS's that way . . . ***while in OSX***  . . . no worries about getting fan control set up with a separate linux install . . . it's all covered by OSX . . . probably much simpler . . . probably would not have to mess with BC or windows.

But, if you are a masochist like me, you would probably have to wipe the whole HD, either from install DVD, recovery disk, or ext FW HD back up . . . then reinstall OSX, reinstall rEFInd; then decide if you wanted to use BC (I didn't, which may mean some OSX features are lost, camera??) set up the extra two partitions, one for windows, one for linux; re-install windows; then try for the 3 partition linux install . . . and then read thru the Mactel FAQ at the top of this sub-forum and figure out whether the heat issues are affecting you and get that set up . . . .

e.

I'm pretty much a masochist as well, but not to the extend of deleting my entire drive! :D I can't find a way to label "bios_grub" when double clicking free space, it just lets me choose MB, format, and select a directory such as "/boot, / , /home" etc. 

However, when looking through my partition drive where i set Xubuntu to install, it did install the necessary files, however only GRUB was missing. may have to manually install GRUB? the files/date were there, but no grub grub.

---

### Post by este.el.paz on 2014-12-30
> **jark_99 said:**
> I'm pretty much a masochist as well, but not to the extend of deleting my entire drive! :D I can't find a way to label "bios_grub" when double clicking free space, it just lets me choose MB, format, and select a directory such as "/boot, / , /home" etc. 

However, when looking through my partition drive where i set Xubuntu to install, it did install the necessary files, however only GRUB was missing. may have to manually install GRUB? the files/date were there, but no grub grub.

In the "format" list should be some ref to "grub" or "bios_grub" . . . select that for the 10 MB partition.  You could try to manually install GRUB, but I recently went thru this problem and it wouldn't "repair" . . . seemed like I had to do the whole install.

Another thing to try, download the "SuperGrub2" iso, and see if you can boot that and use it to boot you install, and maybe you can repair or add GRUB using it, very handy app to have for troubleshooting . . . .

e.

---

