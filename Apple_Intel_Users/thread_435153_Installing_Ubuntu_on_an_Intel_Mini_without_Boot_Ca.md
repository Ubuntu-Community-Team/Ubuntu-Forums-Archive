---
title: "Installing Ubuntu on an Intel Mini without Boot Camp?"
date: 2007-05-06
forum: Apple Intel Users
---

### Post by magus42 on 2007-05-06
I'm looking for a small, quiet replacement for my current linux server, and started eyeing a mac mini, as the price is lower than any comparable mini-itx/shuttle type option I could find :)

However, I'm not finding any info on the possibility of using it without boot camp, since I do not want OSX on the system at all, nor would I want to have to go through extra steps to pick Ubuntu when booting, since it will be headless :)  (I already have another mac mini for OSX)

Apologies if this has been covered somewhere, but all I could find no matter where I looked was info with boot camp :)

---

### Post by benanzo on 2007-05-06
You don't need bootcamp.

Just format the drive and install Ubuntu normally.  GRUB will be written to the MBR portion of the GPT and will boot just fine.

---

### Post by magus42 on 2007-05-06
So grub can handle the non-bios stuff that mac uses? (I forget the name)

If so, that'll make it nice and simple :D

---

### Post by benanzo on 2007-05-06
Apple-Intels use an advanced form of BIOS called EFI.   EFI uses something called the GUID Partition Table (GPT) instead of an MBR.  There are only two bootloaders that I know of that can operate with GPT, GRUB2(formerly PUPA) and ELILO.

From my research I have figured out that on every GUID partition table (gpt) there is an MBR entry as the first block. This is part of the spec from Intel to make EFI compatible with legacy bootloaders (GRUB/LILO/NTLDR) that require an MBR to boot their OS. OS X will boot from an MBR but it wont install to anything other than a GPT. You can get around this by installing it to a GPT disk, then cloning the partition and moving it to an MBR with a legacy bootloader. GRUB can boot OS X even if it's not in an EFI environment.

rEFIt uses a utility called gptsync that syncronizes the partition map between the GPT portion and the MBR portion so that everyone knows about everyone else and there are no surprises and no unbootable errors.

So, if you wipe the entire disk in your Mac and install only Feisty today, you shouldn't get any errors at all. The reason is because Apple updated the EFI firmware awhile ago that allows for limited BIOS emulation including writing an MBR to the disk. GRUB will install to this MBR just fine and boot normally. The only hiccup is that when you first power on your machine you'll have to wait at the grey screen for about 5 seconds and then see the folder with the ? in it (indication that it can't find a bootable disk) until it finally checks the MBR and sees you've got GRUB installed and then Feisty will boot.

I am trying to skip the whole MBR/BIOS emulation business and try to get GRUB2 or ELILO to run right in the EFI environment so that I get them to boot the same as if it were just OS X installed. rEFIt is a great utility and if I were dual booting I would use it, but as of now I've just got Feisty installed and GRUB boots fine after that little wait I told you about.

If anyone has any ideas about ELILO and why the module efivars is not in Feisty so I can use efibootmgr to tinker with the EFI stuff, let me know.

---

### Post by magus42 on 2007-05-07
Wow, that's a lot of good info - thanks a bunch! :D

---

### Post by benanzo on 2007-05-07
No prob, I think the more people know about the EFI/GPT-BIOS/MBR ELILO/GRUB2 issue, the quicker we can get proper support and start booting directly from EFI

---

### Post by ronocdh on 2007-05-07
Benanzo's all over the EFI/BIOS stuff, mad credibility there. But I'd like to add that I recommend you install OS X on a small partition. You can trim down the installation size of OS X by disabling tons of features you don't intend to use, such as foreign languages and iLife applications--you can always add these at any time later with the installer disc, so you're not looking at much space. I recommend you do this because the only way to obtain firmware updates for your hardware (unlocking N-speed capability, for instance) would be via OS X.

You can edit your rEFIt (bootloader) preference to go straight into Ubuntu if you like. =)

---

### Post by magus42 on 2007-05-08
> **ronocdh said:**
> You can edit your rEFIt (bootloader) preference to go straight into Ubuntu if you like. =)

How does one go about things with this method? The minis have more than enough disk space that I wouldn't mind leaving it if there are enough benefits, so long as I can boot directly into Ubuntu :)

---

### Post by benanzo on 2007-05-08
in OS X, edit you /efi/refit/refit.conf and uncomment the #legacyfirst line.

That will boot the first "legacy" OS on your drive first instead of OS X.

---

### Post by entangled on 2007-05-08
An alternative to having a hard disk partition with OSX is to have a bootable backup of OSX on external drive. I did this with Carbon Cloner and it works well for updates.

---

### Post by ronocdh on 2007-05-08
> **entangled said:**
> An alternative to having a hard disk partition with OSX is to have a bootable backup of OSX on external drive. I did this with Carbon Cloner and it works well for updates.
Hm, I like this method. But keep in mind that at each boot, there'll be a 10-15 second delay, as Benanzo has made clear. I personally would much prefer to edit the rEFIt settings (set Ubuntu as primary boot and reduce the countdown to something like 3 seconds) for the sake of bootup speed alone.

---

### Post by magus42 on 2007-05-19
Had to wait a little longer than I anticipated to get ahold of a new mini, but now that I have it... :)

Should I try to resize the existing partition before installing Ubuntu, or just blast it all, partition into 2, then reinstall OSX after Ubuntu and edit the refit conf?

Edit: noticed a few other threads in here, it sounds like I should try to resize from Ubuntu, or use BootCamp to resize, then install rEFIt instead?

Not sure what's easiest

---

### Post by voltagex on 2007-05-19
I'm going down the dual boot road, but once I'm in the Ubuntu CD's bootloader, the keyboard doesn't work. Of course I can just wait but I'd like to know how to use the keyboard so I can specify boot options for the CD.

---

### Post by benanzo on 2007-05-19
> **magus42 said:**
> 
Should I try to resize the existing partition before installing Ubuntu, or just blast it all, partition into 2, then reinstall OSX after Ubuntu and edit the refit conf?

If you want to dual boot with OS X and Ubuntu then it is far easier to install OS X normally, then use Ubuntu to do the partitioning. The rough steps:

1) Wipe the drive
2) Install OS X on the whole drive
3) boot Feisty and resize the OS X paritition to whatever size you want.
4) Install Ubuntu to the rest of the disk
5) Boot into OS X and install refit
6) At the refit boot screen select the partition manager and sync the MBR /GPT

Now your dual boot is set up.

---

### Post by magus42 on 2007-05-19
> **benanzo said:**
> If you want to dual boot with OS X and Ubuntu then it is far easier to install OS X normally, then use Ubuntu to do the partitioning. The rough steps:

1) Wipe the drive
2) Install OS X on the whole drive
3) boot Feisty and resize the OS X paritition to whatever size you want.
4) Install Ubuntu to the rest of the disk
5) Boot into OS X and install refit
6) At the refit boot screen select the partition manager and sync the MBR /GPT

Now your dual boot is set up.

Steps 1 and 2 can be skipped if OSX is already there from the pre-install, yes? Or do I need a fresh install for some reason? :)

Edit: also, will the server CD let me resize it graphically, or should I burn a normal desktop CD for that, then switch to server for the install?

---

### Post by andrego on 2007-05-19
> **magus42 said:**
> Steps 1 and 2 can be skipped if OSX is already there from the pre-install, yes? Or do I need a fresh install for some reason? :)

Edit: also, will the server CD let me resize it graphically, or should I burn a normal desktop CD for that, then switch to server for the install?

Steps 1 and 2 are important if you want to remove all the pre-installed stuff that comes with OS X.  E.x. Garage Band takes 4 GB or so.  Just wipe clean and uncheck everything you won't need installed when you reinstall OS X.  Only takes about 10 min.  Or, you could delete a lot of files out of 
/Applications
/Library/Application Support/

As for resizing, GParted is used, so it's graphical.  Once you boot the livecd, browse through the system menu - it's listed there.

---

### Post by andrego on 2007-05-19
> **ronocdh said:**
> Hm, I like this method. But keep in mind that at each boot, there'll be a 10-15 second delay, as Benanzo has made clear. I personally would much prefer to edit the rEFIt settings (set Ubuntu as primary boot and reduce the countdown to something like 3 seconds) for the sake of bootup speed alone.

Idea: Why not install rEFIt in the 200MB efi partition using OS X, set the legacyfirst option.  Then, boot Ubuntu installer, wipe OS X, and install Ubuntu there.  That way, no OS X, and no delay.  I'd try it to confirm it works...but I like my OS X partition.  Any takers? ;)

---

### Post by magus42 on 2007-05-20
woohoo, it worked! thanks for all of your help, now I just have the loooong process of copying all the data over from the old server :D

---

### Post by pspcz on 2007-07-25
hopefully this is not a dead thread because i could use some advise that appears to be in here..just a bit over my head

i am installing 7.04 i386 on a intel mini (1.66 ghz) for use only as a headless http server

i only need it to boot into ubuntu and i am not really concerned about needing a sliver of osx for firmware updates, this server has only one job and will not be using any drivers etc

from what i can grasp from this thread it appears that prior to installing ubunto i should reformat the disk into the MBR format and than go ahead with the standard ubuntu LAMP install...is that correct? 

and lastly..do I need to install GRUB or rEFIt or is that only an issue if I was keeping the EFI formatted disk and or dual booting?

thanx in advance

Pz

---

### Post by cyberdork33 on 2007-07-25
> **pspcz said:**
> hopefully this is not a dead thread because i could use some advise that appears to be in here..just a bit over my head

i am installing 7.04 i386 on a intel mini (1.66 ghz) for use only as a headless http server

i only need it to boot into ubuntu and i am not really concerned about needing a sliver of osx for firmware updates, this server has only one job and will not be using any drivers etc

from what i can grasp from this thread it appears that prior to installing ubunto i should reformat the disk into the MBR format and than go ahead with the standard ubuntu LAMP install...is that correct? 

and lastly..do I need to install GRUB or rEFIt or is that only an issue if I was keeping the EFI formatted disk and or dual booting?

thanx in advance

Pz

Just tell Ubuntu to "Use the entire disk" during the install and you shouldn't have a problem.

---

### Post by pspcz on 2007-07-25
> **cyberdork33 said:**
> Just tell Ubuntu to "Use the entire disk" during the install and you shouldn't have a problem.


as in dont sweat the MBR and Grub stuff...just install on the whole disk and I should be in good shape?


Pz

---

### Post by cyberdork33 on 2007-07-25
that would "erase" all the stuff there currently, and replace it with an MBR as is the default. Grub will be installed in the MBR as usual.

---

### Post by benanzo on 2007-07-25
***pspcz***:

If you're not planning to do anything tricky with multi-booting then installing Ubuntu by just accepting the default options in the install menu will work just fine.  There is no need for rEFIt or any GPT/MBR voodoo.  Just boot the LiveCD, click Install and accept the defaults.  You'll be up and running in no time.

---

### Post by pspcz on 2007-07-25
thanx guys, i am perhaps guilty of thinking too much

i am not really into experimenting..these things are just tools to me, i prefer to just be prepared, get things done right the first time and move on

your info will help greatly


Pz

---

### Post by pspcz on 2007-07-26
as predicted by bonanzo and cyberdork the install was very straight forward, just pop in the cd use the whole disk and set up network

the only weird issue i am having is that the computer will boot up fine with a monitor attached, if i shutdown and remove the monitor and restart to administer through ssh it never comes up

i am not sure if the boot is hanging or never happening, apache doesnt come online either


Pz

---

### Post by cyberdork33 on 2007-07-26
ah yes I remember something about this. The Mac Mini won't work correctly unless (it thinks) there is a monitor attached. There are some pins you can connect on the video out or something to trick it. 

This guy outlines using a resistor, although it sounds like the system is running fine, he just can't get a remote desktop.... odd though that might only apply in OSX... Ubuntu may be getting some other error because of it.

[http://blackfriarsinc.com/blog/2007/04/how-to-keep-headless-mac-mini-happy](http://blackfriarsinc.com/blog/2007/04/how-to-keep-headless-mac-mini-happy)

I have no idea if this will fix your problem, but it might be worth trying.

---

### Post by pspcz on 2007-07-26
i contacted my colocation facility (macminicolo.net) to ask if they knew of this issue and they referred me to Dr Botts for this part <http://www.drbott.com/prod/db.lasso?code=0153-GHDD>

according to dr bott this should solve the problem, i will post in a few days if it works or not

blackfriars solution looks pretty scary as do the other similar solutions i have seen online, i cant have some temporary hack, either this dongle works or we stick with using OSX server


Pz

---

### Post by cyberdork33 on 2007-07-26
yea I have seen those, but how can you justify a $30 adapter when you can use a $0.05 resistor. If sticking it in the socket is "risky" then solder it on the inside to the connector (maybe even with a switch so you can disconnect it).

---

