---
title: "Feisty CD won't boot."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by harerama on 2007-04-20
Greetings,

1,I burned cd following the instruction correctly.

>    1.Insert a blank CD into your burner. A "CD/DVD Creator" file browser will pop up. Close this browser as we will not be using it. (Edgy will say "Choose Disk Type", click 'Ignore")
   2. Find the downloaded ISO image in the file browser (available at Places &#8594; Home menu on top of the screen.) Right click on the ISO image file and choose Write to Disc and wait for burning to complete.


2,I also verified CD ,which I burned, following instruction here.

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

But CD won't boot. I tried many times sometimes the cd asked my to type username and other times just failed.

I have already wasted two CDs. Why do you think this happened to me? Any solutions? I should probably discard files and download another files and try again?
PS,
There aren't ubuntu hashes for Feisty yet to do md5sum are there?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Thanks

---

### Post by ogroef on 2007-04-20
Hi

Did you find any ubuntu checksum hashes for the 7.04 release.

Regards

---

### Post by xyz on 2007-04-20
I'll think about this but in the meantime, think of using CD-RW CD's if like me, you're short on CD's or just hate to waste them.
Once you're sure, burn it to a regular CD.

---

### Post by raspark on 2007-04-20
Hi,

Since you have verified the integrity of the CD, do you know if your computer will boot from *any* CD?

If not then you'll have to change the boot settings in the BIOS so that boot from CD is before boot from hard disk.

Have you ever checked, or changed any of the BIOS settings?  Check with your computer manufacturers, website and/or computer documentation on how to get into the BIOS, it's usually a function key when the computer is starting up.

---

### Post by Ownerizer on 2007-04-20
> **harerama said:**
> 
There aren't ubuntu hashes for Feisty yet to do md5sum are there?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Thanks

Yes, according to [release.ubuntu.com]("http://releases.ubuntu.com/7.04/"), here are the MD5 hashes that you should get if your download was intact.

50f3655fbcbdba9746d4b05ad8705b0b *ubuntu-7.04-alternate-amd64.iso
ff0cc7c9ed5157f0ff8c0f2213973f49 *ubuntu-7.04-alternate-i386.iso
a2b159599b69cea51371eee1ec5feda6 *ubuntu-7.04-desktop-amd64.iso
e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso
8a1099f5fa8eaf4ee295bf0087c8b03a *ubuntu-7.04-server-amd64.iso
cf462501e2dc1b82b96dfc497a0404a2 *ubuntu-7.04-server-i386.iso
e016f1e3322848af98d01eae2688568c *ubuntu-7.04-server-sparc.iso

If your MD5 doesn't match, download the ISO again, perhaps from a different mirror or torrent. :-)

---

### Post by xyz on 2007-04-20
[Access/Enter Motherboard BIOS]("http://www.michaelstevenstech.com/bios_manufacturer.htm")

---

### Post by Johnny_Too_Bad on 2007-04-20
I'm having the same problem.  

Downloaded the ISO, burned the CD at 4x, verified it, put it in the tray, restarted computer, went into BIOS and changed the order so Boot to CD comes first, let it start up, and yet NOTHING HAPPENS.  It just goes right to the desktop without doing anything on the CD.  What's going on?

Please keep in mind I'm a total beginner to Linux.  Also, if it's anything, I am running on Dapper.

---

### Post by joshjani on 2007-04-20
FWIW, I too thought I downloaded a proper copy of the ISO for Feisty, but after I had ruined 2 cd's without success I looked at my file and saw it was only 14mb. The other live cd .iso's I had for Xubuntu and Edgy were well over 600mb, more proper for a full cd install. 

I forget now which mirror I used to download my first, but I'm now downloading from Penn State, and it looks to be the full file. 

Just a suggestion from a total noob, but just check to make sure you actually have a good iso downloaded.

---

### Post by harerama on 2007-04-20
Cheers,

There seems to be a bung in the program.

[http://ubuntuforums.org/showthread.php?t=415041](http://ubuntuforums.org/showthread.php?t=415041)

I'll see what happens.

---

