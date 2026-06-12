---
title: "Major Install Problem"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by OldManRiver on 2007-08-06
All,

Tried 6 time to install ubuntu.  Clear disk 3 times with Partion Commander.  Everytime system gets to **REBOOT** it hangs with **LI** at the command prompt.

Can anyone help?

OMR

---

### Post by Zedd on 2007-08-06
What are the system specs? What version of K/X/Ubuntu are you trying to install?

---

### Post by OldManRiver on 2007-08-07
All,

The ISO file I downloaded, per the instruction for installation is "ubuntu-7.04-desktop-i386.iso"

Should I have a different file?

Hardware is:

MB  = ECS 755-A2
RM  = 1GB
HD1 = Samsung  SV0431 4.3GB
HD2 = Seagate   ST3400 40GB
PS   = Echo Star 580W
VIC = Jaton TVGA9685PCI
MON = AMW MR19C-AB

Once I have this running plan to add 200G Sata drive replacing the Samsung.

OMR

---

### Post by schorsch on 2007-08-07
It seems you are using LILO as bootloader and not GRUB, which is the default, right? Do you have any raidsets in your system?

---

### Post by Inxsible on 2007-08-07
How did you burn the CD, as a data CD or an iso image?

You should be burning it as an iso image, which will give you a Live CD. Remember to burn it at speeds of 4x or less. After burning it, it would be a good idea to check the CD integrity.

---

### Post by OldManRiver on 2007-08-07
> **schorsch said:**
> It seems you are using LILO as bootloader and not GRUB, which is the default, right? Do you have any raidsets in your system?

NO, But MB has a raid set on it, I'll check BIOS to see if it thinks it is enabled.  Also had Red Hat on this prior and it uses LILO to boot, maybe there is something it set that needs undoing?

OMR

---

### Post by OldManRiver on 2007-08-07
> **Inxsible said:**
> How did you burn the CD, as a data CD or an iso image?

You should be burning it as an iso image, which will give you a Live CD. Remember to burn it at speeds of 4x or less. After burning it, it would be a good idea to check the CD integrity.

Used MagicISO to burn CD.  Always works when the others fail.

OMR

---

### Post by Inxsible on 2007-08-07
> **OldManRiver said:**
> Used MagicISO to burn CD.  Always works when the others fail.

OMR @ what speed ?

---

### Post by OldManRiver on 2007-08-07
> **Inxsible said:**
> @ what speed ?

Either 8x or 16x, (CD burn max at 48x) but reading and running .iso is not or does not seem to be problem.

It is the installed S/W that is funky, unless you suspect bad read of source on the CD.

OMR

---

### Post by Inxsible on 2007-08-07
> **OldManRiver said:**
> Either 8x or 16x, (CD burn max at 48x) but reading and running .iso is not or does not seem to be problem.

It is the installed S/W that is funky, unless you suspect bad read of source on the CD.

OMRI am not saying it might be a problem with you per se, but I have seen a lot of people who burnt disks at high speed and then had problems installing.

---

### Post by OldManRiver on 2007-08-07
All,

Reburnt the CD and trying a re-install.  If it fails will look at the scenario below:

Checking one thing, I selected the maximum single partion option in the install, which I think selected the Seagate drive.  However I think the Samsung is set as Master, so maybe I need to change the Master/Slave hardware config with the drive jumpers?

What do you think?

OMR

---

### Post by OldManRiver on 2007-08-07
All,

Re-install failed again, so had to change the HDs.

Since I had to phyically remove HDs, I upgraded with a HD laying around the shop, to:

Hardware now is:

MB = ECS 755-A2
RM = 1GB
HD1 = Seagate ST3400 40GB
HD2 = Seagate ST3800 80GB SATA
PS = Echo Star 580W
VIC = Jaton TVGA9685PCI
MON = AMW MR19C-AB

Had to change BIOS setting to enable SATA, and now having to re-install for BOOT loader.  Selected "Guided - Entire Disk" for partitioning option (hdb).

OMR

---

### Post by Zedd on 2007-08-07
Try installing with only one hard drive plugged in. I have had problems where it would install to one hard drive, and write GRUB to the MBR of another hard drive. Of course, this was fixed by booting to the other hard drive when the install was complete, but the easiest way to make it install correctly is by only having one hard drive connected. You can always set up the other ones manually when everything is working correctly.

---

### Post by OldManRiver on 2007-08-07
All,

Install still fails!

OMR

---

### Post by OldManRiver on 2007-08-08
Now even Partition Commander will not boot!

Help!!!

OMR

---

### Post by Zedd on 2007-08-08
Which drive were you planning on installing Ubuntu to? The 40 GB or the 80 GB? Also, does the other drive have any important files on it, or would you be willing to attempt to install to that drive.

Either way, unplug all hard drives except the one you want to install to. Then boot to the live CD and install. When you get to the partitioning step, set up your system manually. I would suggest this setup: 
1GB primary ext2 /boot 
2GB primary swap 
12 GB extended ext3 / 
25/65GB extended ext3/reiserfs /home

For your /home partition it depends on which drive you installed to. It'll be roughly 25 GB if you used the 40 GB and roughly 65 if you used the 80 GB. Either way, tell it to use all of the remaining space. 

Then you can choose whether you want to use ext3 or reiserfs. If you're not sure, just use ext3.

That should do it. Report back with problems!

---

### Post by OldManRiver on 2007-08-08
All,

Question:

My HD always shows as hdb, with only the SeaGate ST3400 in the system.

Isn't it suppose to show as hda?

What ever it is doing this, is screwing my install.

OMR

---

### Post by OldManRiver on 2007-08-08
Fix this problem.

Had HD pin shorting lead next to pwr connector.  Master is furthest from pwr connector.

Label was on upside down so lost the translation.

Now having X.win res problem.  The Jaton VIC has Trident chipset, but having trouble with memory config.

OMR

---

### Post by Zedd on 2007-08-09
Sorry, didn't quite understand that last post. You have Ubuntu installed successfully? Are you having problems with your video card? If you are, post the output of "lspci -v" and "cat /etc/X11/xorg.conf"

---

### Post by OldManRiver on 2007-08-09
All,

Worked with IRC and got install up, X.win res steady (monitor was causing problems above depth=15.  Found searching web that I need to open a bugzilla with Xorg for this monitor, had problem with it on Gentoo also), CUPS installed.  Now need to install Samba.

What is cmd to check status of loaded drivers.  On Gentoo "rc-status" showed list of all loaded modules such as dhcp, hald, cups, samba, etc. and whether they loaded OK or with errors.

I need to run cmd here to see if samba is loaded, else I need to use a cmd it install.  I presume cmd is: "sudo apt-get install samba".

Am I correct?

OMR

---

### Post by splintercellguy on 2007-08-09
Yes :).

---

### Post by OldManRiver on 2007-08-09
> **splintercellguy said:**
> Yes :).

S,

Ran command and samba is up and running seeing network, but defaulted to "WorkGroup=MSHome".  I suppose edit of smb.conf to change is in order?

Also asked about "status" cmd.  Do you know it?

OMR

---

### Post by OldManRiver on 2007-08-09
All,

Samba works, can see all the windows share, from network, but click on or try to open, that a diff story.  Not working at all there.  Comes up with login screen to Windows and does not accept the windows UID, Domain, and PWD.

Also when on Win side of network, also can not see or open Ubuntu shares.  Computer shows in domain list but attempt to open or click also giving login screen that will not validate, so login fails.

Any ideas?

OMR

---

### Post by OldManRiver on 2007-08-10
All,

Got this partially fixed.  See thread at:

[http://ubuntuforums.org/showthread.php?t=522402](http://ubuntuforums.org/showthread.php?t=522402)

Still need help though with Win looking into U box.

Thanks!

OMR

---

