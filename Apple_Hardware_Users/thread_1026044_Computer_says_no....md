---
title: "Computer says no..."
date: 2008-12-30
forum: Apple Hardware Users
---

### Post by rektruax on 2008-12-30
I got the first of the macbook 1,1's. It's really been an awesome system thus far. Last year my 4 year old shoved something into the superdrive, so I just disabled it, and got a nice Lacie firewire superdrive... Well I imagine you can guess what's next. I'm trying to boot 8.04 from the external disc drive, but the "computer says no..."

Anybody have a work around to this legacy firewire discrimination? Any help would be peachy.

---

### Post by cyberdork33 on 2008-12-30
can you go into more detail on what you tried? Do you have rEFIt installed?

---

### Post by leeai on 2008-12-30
Has anyone bought this type of sling shot before that holds the amo in the handle? [http://www.liangdianup.com/sporting_1.htm](http://www.liangdianup.com/sporting_1.htm) 
this company has free shipping to anywhere in the world and they guarantee delivery to Australia. I heard that sling shots 
are ok to sell in Australia as long as you say they are being used to toss bait in the water when you go fishing, any truth 
to thatone?

---

### Post by rektruax on 2008-12-31
> **cyberdork33 said:**
> can you go into more detail on what you tried? Do you have rEFIt installed?

Oh yes... The rEFIt boot screen comes up, and upon choosing Tux, she either freezes, I get the black and blue "no legacy OS from firewire allowed", or there's simply a flashing folder with a question mark. All results that others have discovered. I couldn't even install Linux as the sole OS if I wanted to.

Since posting this, I've scoured the web in search of a solution both at Linux, and Mac forums and while there's quite a bit of discussion on this matter the general consensus is there's no getting around the Mac firmware shortcoming. I've concluded that there isn't a simple work-around.

If you know differently, please advise. Otherwise, thank you for the response...

---

### Post by cyberdork33 on 2008-12-31
You might be able to install grub-efi and boot from there. There are a few recent threads on getting it setup, but they are not for the linux newbie. I think that is the only method that will work in your situation though until the "no legacy OS from Firewire (or USB)" issue is resolved.

[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

PS Use the latest version of Ubuntu! version 8.10 (Intrepid Ibex)

---

### Post by rektruax on 2008-12-31
> **cyberdork33 said:**
> You might be able to install grub-efi and boot from there. There are a few recent threads on getting it setup, but they are not for the linux newbie. I think that is the only method that will work in your situation though until the "no legacy OS from Firewire (or USB)" issue is resolved.

[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

PS Use the latest version of Ubuntu! version 8.10 (Intrepid Ibex)


I've looked over the thread you referenced... Daunting but not impossible? However, there's no evidence that Macbook build 1,1 will work, and I probably lack the skills to be the guinea pig. It's seeming more likely for me to simply swap macbooks with the wife. Hers doesn't suffer from my 4 year olds before mentioned "modification".

Thanks so much for your support...

---

### Post by cyberdork33 on 2008-12-31
> **rektruax said:**
> I've looked over the thread you referenced... Daunting but not impossible? However, there's no evidence that Macbook build 1,1 will work, and I probably lack the skills to be the guinea pig. It's seeming more likely for me to simply swap macbooks with the wife. Hers doesn't suffer from my 4 year olds before mentioned "modification".

Thanks so much for your support...
ah, well if you have another mac in the house, then you can start your "broken" mac in Target Disk Mode and hook it up to your wife's mac and partition the drive and install from there. Might take a little extra work getting things working after that, but I think that is a valid path to take. (of course you might mess up the MBR on your wife's mac doing that, but it can be repaired. [http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677) )

---

### Post by rektruax on 2008-12-31
> **cyberdork33 said:**
> ah, well if you have another mac in the house, then you can start your "broken" mac in Target Disk Mode and hook it up to your wife's mac and partition the drive and install from there. Might take a little extra work getting things working after that, but I think that is a valid path to take. (of course you might mess up the MBR on your wife's mac doing that, but it can be repaired. [http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677) )

I have 3 more Mac's in the house. A iMac like yours, a G4 tower, my wife's macbook, and mine. Which do you think would be the best candidate to attempt this Target Disc Mode approach? You're being most patient, and it is appreciated...

---

### Post by cyberdork33 on 2009-01-02
> **rektruax said:**
> I have 3 more Mac's in the house. A iMac like yours, a G4 tower, my wife's macbook, and mine. Which do you think would be the best candidate to attempt this Target Disc Mode approach? You're being most patient, and it is appreciated...

well, the PPC mac probably would not work well, and in an attempt to prevent problems on your wife's machine, I'd use the iMac.

Overview of procedure:
BACKUP DATA! and [create a refit CD, or install it on a USB drive]("http://refit.sourceforge.net/doc/c1s1_install.html"). 
1. First Use Bootcamp / Disk Utility on your target Mac to create space to install Ubuntu. (Just create a fat32 or msdos partition for now).
2. Start target Mac in Target Mode (hold t on startup)
3. Connect Target Mac to Powered Down iMac with firewire cable
4. boot iMac form Ubuntu LiveCD
5. Start System > Administration > Partition Editor (gparted).
6. BE CAREFUL HERE. You need to make sure you work on the correct hard drive. The primary disk should be the iMac internal drive (probably /dev/sda), the secondary drive should be the FIrewire connected Mac (probably /dev/sdb). Make sure you are editing the firewire device.
7. With the right disk selected, you should see three partitions. An EFI partition, an HFS+ partition (OSX), and your new partition you created for Ubuntu. Select the new partition and delete it. This will leave free space. Apply and exit the partition editor.
8. Start the Ubuntu installer. When prompted, you will need to choose the location to install Ubuntu. Make sure you choose the correct hard drive again (probably /dev/sdb) and if the option is available, choose to install to the "largest free space" on the second drive. If that is not available, you will have to manually create the Ubuntu partition first. If you need help with that, just post back.
9. Just before Ubuntu begins installing, it will give a summary of the changes you are about to make. Verify the disks that will be modified. On the same screen, click the "Advanced" button and choose to install to the root partition. most likely, this will be /dev/sdb3.
10. After it is finished, your iMac may have a problem booting. If this is the case, put in the refit CD or USB drive and boot the iMac. rEFIt should start and you can use the partition tool at the bottom to sync the partition tables and get the iMac booting again. You might also need to do this on the target mac as well.

Good Luck!

---

