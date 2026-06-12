---
title: "Dual boot on 2 SATA HDs"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Europa2010AD on 2007-03-16
I'm planning to install Ubuntu in one of my SATA drives that doesn't have WinXP installed. I've searched the forum but it seems like there are only threads about SATA+IDE drives but not SATA+SATA setup. 

Since I am planning to unplug the HD w/ winXP in it before I run the Ubuntu installation, is there anything I should know before I go ahead? And what about after the installation when I plug the winXP HD back in, do I have to make any modification to the GRUB menu.lst as pointed out in those SATA+IDE threads?

Thanks for the help!

---

### Post by Najand on 2007-03-16
What is the reason you are planning to unplug the HD w/ winXP in it before I run the Ubuntu installation? If you do so you must configure grub by yourself for sure.

---

### Post by Europa2010AD on 2007-03-16
> **Najand said:**
> What is the reason you are planning to unplug the HD w/ winXP in it before I run the Ubuntu installation? If you do so you must configure grub by yourself for sure.

Oh... I read it in one of the threads that it's safer this way -- just in case something screws up during installation, my winXP HD won't be affected at all. So do you think this step is unnecessary? Is it safe for me to install Ubuntu with my winXP HD plugged in?

---

### Post by hyper_ch on 2007-03-16
Yes it is safe... the only thing you ahve to be carefull about is that you select the correct harddisk to install ubuntu to...
I recommend that you totally partition your winxp harddisk (well I guess it already is) so that there is no unallocated space left...
The "ubuntu" harddisk on the other hand leave that one unpartitioned or delete existing partitions on that drive.
This way it should be fairly simple to tell which one is which harddisk :)

---

### Post by xadder on 2007-03-16
I have two SATA hds, and had no problems at all. (I even had the infamous Jmicron controller which almost no other distribution could deal with). I don't have any Windows stuff, but I installed Ubuntu dual-boot with the older gentoo installation without problems.

---

### Post by halw on 2007-03-16
Yes. You can install Ubuntu on a second drive without disconnecting your XP hd. I've done it. No muss, no fuss.

---

### Post by Europa2010AD on 2007-03-16
I see. Thanks for the help guys! Your answers have really made me a lot less worried about taking the big step into setting up a dual boot machine. I'll report back my progress after the setup is done! (well perhaps I should go get some sleep first before that...)

---

### Post by hyper_ch on 2007-03-16
Well, the only thing that can go wrong in my opinion is that you select the wrong disk to install it to... however if one is totally partitioned and the other is not and/or if they are of different sizes then you should - with normal attention - have no problems selecting the right disk :)

---

### Post by gn2 on 2007-03-16
Just be careful where to install Grub, ideally you don't want to overwrite the Windows MBR.

To be absolutely certain this doesn't happen you can disconnect the power to the drive with Windows on it.

To select OS press F2, F8 or whatever to bring up the Boot Device Selection Menu.

---

### Post by hyper_ch on 2007-03-16
why not overwriting the windows mbr? for dual boot it doesn't matter....

---

### Post by Europa2010AD on 2007-03-16
> **hyper_ch said:**
> why not overwriting the windows mbr? for dual boot it doesn't matter....

I read it somewhere that says if something goes wrong with the GRUB installation and the windows MBR gets overwritten, it's really hard to fix it. Dunno if it's true or not.

---

### Post by steve101101 on 2007-03-16
THIS IS HOW YOU DO IT. I first had Windows XP on my first hard drive. I then installed Ubuntu on the second HD. After that i made Ubuntu the master drive and windows the slave drive. Then just boot into Ubuntu.

```

cd /boot/grub
sudo gedit menu.lst

```

in this file go to the bottom and add this...

```

title                Windows XP
rootnoverify    (hd1,0)
savedefault
makeactive
map               (hd0)   (hd1)
map               (hd1)   (hd0)
chainloader    +1

```

then when your booting up press escape when the words "Grub" come on. press down until windows xp is highlighted and press enter. it will then boot into windows.

If you have any questions just Private Message me.

---

### Post by cavemanf16 on 2007-03-16
Overwriting the Windows MBR only matters if you ever want to go back and completely remove Ubuntu from your system. Grub overwrites MBR anyway, so disconnecting the 1st HDD will only cause you more manual work later when you wish to automatically enable the Windows disk for reading data from it.

---

### Post by Europa2010AD on 2007-03-16
> **cavemanf16 said:**
> Overwriting the Windows MBR only matters if you ever want to go back and completely remove Ubuntu from your system. Grub overwrites MBR anyway, so disconnecting the 1st HDD will only cause you more manual work later when you wish to automatically enable the Windows disk for reading data from it.

Well I guess what I am trying to do is to install Ubuntu + GRUB on my 2nd HD (I'm using the Alternate install CD, so that'll give me the option where to install GRUB, correct?), and then in BIOS choose to boot from the 2nd HD. This way the MBR in my 1st HD where winXP is will remain intact, and if something screws up in GRUB / Ubuntu, I can just boot form the 1st HD into windows...

Do you think this will work?

---

### Post by confused57 on 2007-03-17
> **Europa2010AD said:**
> Well I guess what I am trying to do is to install Ubuntu + GRUB on my 2nd HD (I'm using the Alternate install CD, so that'll give me the option where to install GRUB, correct?), and then in BIOS choose to boot from the 2nd HD. This way the MBR in my 1st HD where winXP is will remain intact, and if something screws up in GRUB / Ubuntu, I can just boot form the 1st HD into windows...

Do you think this will work?
Set your bios to boot the hard drive you'll be installing Ubuntu on to boot first, before booting up the alternate cd to install.

If you want to be absolutely sure grub gets installed to your sdb mbr, near the end of the installation, you'll be give the option to install grub to (hd0) mbr(which should be sdb, since you selected it to boot first)...if you want to be absolutely sure, select "no", then you'll be presented with another screen where you can specify to install grub to /dev/sdb.

See the first link in my signature for some excellent screenshots using the alternate cd.

---

### Post by bonedog73 on 2007-03-18
Simialar question, I'm trying to install Ubuntu on my MSI K9A Platinum mobo with SATA II. But Ubuntu doesnt see my Seagate 320g xp drive nor my Maxtor 200g drive. 

Anyway to get Ubuntu to work with these drives, or is SATA not compatible with Ubuntu?

---

### Post by Europa2010AD on 2007-03-31
> **bonedog73 said:**
> Simialar question, I'm trying to install Ubuntu on my MSI K9A Platinum mobo with SATA II. But Ubuntu doesnt see my Seagate 320g xp drive nor my Maxtor 200g drive. 

Anyway to get Ubuntu to work with these drives, or is SATA not compatible with Ubuntu?

I dunno about SATA II, but my two harddrives connected through SATA are working fine in my brand new Ubuntu installation! :-)

---

### Post by jimrz on 2007-03-31
> **bonedog73 said:**
> Simialar question, I'm trying to install Ubuntu on my MSI K9A Platinum mobo with SATA II. But Ubuntu doesnt see my Seagate 320g xp drive nor my Maxtor 200g drive. 

Anyway to get Ubuntu to work with these drives, or is SATA not compatible with Ubuntu?

I have 2 SATA II drives on this machine and ubuntu (dapper + edgy + fiesty) see and work with both. The only issue I had installing was that something in my BIOS did not play well with GRUB causing errors that did not allow either side to boot. This was solved by unplugging the the xp drive, plugging the ubuntu drive into the first SATA slot, redoing the install and the plugging the xp drive back into another SATA slot.  There was no problem then mounting the various partitions on the xp drive. Also, I have found that using f12 to select the proper drive (on the rare occassions that I boot xp) takes only a couple of seconds longer and requires fewer keystroks than doing so via GRUB, so I have not bother to even add xp to my GRUB menu.

---

### Post by SentientFluid on 2007-04-03
> **hyper_ch said:**
> why not overwriting the windows mbr? for dual boot it doesn't matter....

Right after my computer POSTs but before it identifies my hard drives, I can press F11 to open a boot menu.  This menu allows me to select which disk drive I want to boot to.  I can choose any hard drive or CD drive in my system.

So, if Windows is on a different physical drive, and I don't overwrite the Windows MBR, then I can still use this menu to choose which drive to boot from.  It's faster than going through Grub, and since it can bypass Grub and go straight to the Windows MBR, when I mess things up I can still boot into Windows and find out how I can fix it.

Did that make sense? :)

---

