---
title: "Ubuntu help please"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Bunnytard on 2007-08-26
Hello im a total noob to linux and ubuntu and i have a question. Is it possible to have both ubuntu and windows vista? Like if i use ubuntu today will i be able to use windows vista the next day? And If i download ubuntu will i still have windows vista? Thanks for the help :)

---

### Post by oilchangeguy on 2007-08-26
> **Bunnytard said:**
> Hello im a total noob to linux and ubuntu and i have a question. Is it possible to have both ubuntu and windows vista? Like if i use ubuntu today will i be able to use windows vista the next day? And If i download ubuntu will i still have windows vista? Thanks for the help :)

yes.
and yes, if done properly.

---

### Post by Hobo Joe on 2007-08-26
> **Bunnytard said:**
> Hello im a total noob to linux and ubuntu and i have a question. Is it possible to have both ubuntu and windows vista? Like if i use ubuntu today will i be able to use windows vista the next day? And If i download ubuntu will i still have windows vista? Thanks for the help :)

Yes and yes.

It's quite simple too. :)

---

### Post by KIAaze on 2007-08-26
Ubuntu+XP:
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

Ubuntu+Vista:
[http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx]("http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx")
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

---

### Post by steveneddy on 2007-08-26
You should search the forums for posts related to dual booting with Vista. It is a little trickier than other Windows OS's I've read.

Other things you should be familiar with are:

1. Burning an ISO CD image.
2. Partitioning a hard drive
3. Know how large your hard drive is
4. How to access your BIOS (may not be necessary)

Be ready to learn, because you are about to go down the rabbit hole to see how deep it gets, noobie.

Welcome to the world of Linux.

---

### Post by Hobo Joe on 2007-08-26
> **steveneddy said:**
> 
Be ready to learn, because you are about to go down the rabbit hole to see how deep it gets, noobie.

Welcome to the world of Linux.

Haha, don't scare him away before he even tries it! :P

---

### Post by Bunnytard on 2007-08-30
Ok I burned the cd but whenever I try to boot it, it won't work. I'm guessing I didn't make the cd bootable? Would anyone mind explaining me how to make my cd bootable thanks. :confused:

---

### Post by loaderboy on 2007-08-30
What did you burn the cd with? (software) Insert the cd and right click and check properties, Just to make sure that you didn't just burn the .iso file to the disk.

---

### Post by Bunnytard on 2007-08-30
> **loaderboy said:**
> What did you burn the cd with? (software) Insert the cd and right click and check properties, Just to make sure that you didn't just burn the .iso file to the disk.

I used infra recorder and what do I do to download the image to the cd? Sorry I am absolutely new to Linux xD

---

### Post by kevindubrow on 2007-08-30
Have you tried following the steps on this link:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Good luck.

---

### Post by Bunnytard on 2007-08-30
Yes I have tried that but it still won't work...:(

---

### Post by Pumm4 on 2007-08-30
Make shure your boot seqence is set as:  Floppy > CD/ROM > Disk ...

---

### Post by kevindubrow on 2007-08-30
In the event that your BIOS is set up so that the CDROM is loaded before your hard drive (or you don't know how to check), just explore the CD in Windows and tell us the contents of the CD. If just the .iso file got burned, the CD will not boot.

---

### Post by Bunnytard on 2007-08-30
> **kevindubrow said:**
> In the event that your BIOS is set up so that the CDROM is loaded before your hard drive (or you don't know how to check), just explore the CD in Windows and tell us the contents of the CD. If just the .iso file got burned, the CD will not boot.

The iso cd just got burned. So how do I make it bootable?

---

### Post by ericmitz on 2007-08-30
> **Bunnytard said:**
> The iso cd just got burned. So how do I make it bootable?

If you burned it as a true ISO, it should be bootable without doing anything further

---

### Post by Pumm4 on 2007-08-30
> **Bunnytard said:**
> The iso cd just got burned. So how do I make it bootable?
If it fails when rebooting with this CD inside your computer then do this....

Restart your computer and keep pressing Del. button until the BIOS setupn screen apears.

To change the boot sequence in an AWARD BIOS, look for the *BIOS FEATURES SETUP *entry. Other manufactures may have a different name to this, such as *ADVANCED CMOS SETUP*. When you have found the entry, select it and confirm with "Enter".

In the screen that opens, look for a subentry called *BOOT SEQUENCE*. Now change it as (I've) mentioned above...

---

### Post by KIAaze on 2007-08-30
On some computers it's F2 or F8 to enter the BIOS setup. ;)
There is usually a line telling you how to enter BIOS setup at startup (careful, it can go by very quickly).

---

### Post by loaderboy on 2007-08-30
> **ericmitz said:**
> If you burned it as a true ISO, it should be bootable without doing anything further

If you burned it as an ISO file you just have an ISO file on a cd. Not bootable.

---

### Post by Pumm4 on 2007-09-01
> **loaderboy said:**
> If you burned it as an ISO file you just have an ISO file on a cd. Not bootable.
[http://screencasts.ubuntu.com/Downloading_and_Burning_an_Ubuntu_ISO](http://screencasts.ubuntu.com/Downloading_and_Burning_an_Ubuntu_ISO) [IMG]http://www.mysmiley.net/imgs/smile/winking/winking0050.gif[/IMG]

Did it work/help?

---

