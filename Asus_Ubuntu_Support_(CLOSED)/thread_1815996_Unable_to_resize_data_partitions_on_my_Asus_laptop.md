---
title: "Unable to resize data partitions on my Asus laptop"
date: 2011-08-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by linuxforartists on 2011-08-01
Nice to see a dedicated forum for Asus, they're my favorite computer brand.

My machine is an Asus Bamboo laptop that I bought at Best Buy in the United States.  For exact tech specs, you can see this detailed [review on Hot Hardware]("http://hothardware.com/printarticle.aspx?articleid=1544").

I wanted to install either Pinguy OS or Linux Mint, for that improved "out of the box" readiness.  Some people at a Linux user group advised me to set my data partitions manually like this:

NTFS (Windows): whatever amount I prefer
/ (root): 15-20GB for the Linux distro
SWAP: 4GB or twice my RAM (it's 4GB)
/home: the remainder of my hard drive

They also said to make these partitions "logical" because I couldn't have more than 4 primary partitions, whereas logical partitions were unlimited.  Where is the setting for that?

Anyway, they said this partitioning scheme would allow me to dual-boot Windows 7 and Linux.  I wanted this in case there's some app I need in the future for Windows.  The other benefit was that I could upgrade the Linux distro with clean installs, and not wipe out my documents, music, etc. in my Home folder every time.  So I'd get the benefit of future Linux upgrades and preserve my data as well.

The problem is that when I try to to resize the partitions, it doesn't seem to work.  This is using the partition manager in the Ubiquity installer found in Ubuntu and its derivatives.  I haven't tried using GParted yet. 

The first thing I tried to do was shrink the NTFS partition to 100GB (my hard drive is 640GB).  It looked like it was processing fine.  But when it finished, the partitions were still unchanged.  I tried to install Pinguy OS first, when that failed I tried Linux Mint.  With both, I got stuck at the partitioning stage and had to quit the installs.

Is this a hardware problem or a Windows problem?  

The next time I started up Windows, there was an error and it ran though a file check on my hard drive.  Luckily, Windows booted up okay.    

Sorry for how long this post was, I wanted to share all the details so the community could have enough information to suggest solutions.  Does anyone know a good step-by-step tutorial I could follow?  

I've been missing that Linux goodness.

---

### Post by shubham1 on 2011-08-01
should should try using gparted you can convert some softwares of windows to linux by wine.gparted will allow you to resize the partion.

---

### Post by shubham1 on 2011-08-01
some urls gparted.sourceforge.net
[http://www.ubuntux.org/how-to-install-partition-editor-gparted](http://www.ubuntux.org/how-to-install-partition-editor-gparted)
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by shubham1 on 2011-08-01
let me tell what happen when i tired to setup ubuntu with windows.
i start the setup light gone i have to close it.
no linux was installed i opended windows only 1 partion of my 5 partion was lost only 80gb of 500gb.
second time i did my ubuntu installed but windows was lost but files were there.there were many problems in ubutnu so ireinstalled it.but now id dont windows as ubuntu has every thing i want.

---

### Post by ajgreeny on 2011-08-01
Firstly, I suggest you never shrink a windows7 partition with the ubiquity installer or gparted.  It is much safer to use the disk management utility that is available in windows itself.

Having done that you can use gparted on the live CD/USB of ubuntu to make new partitions in the unallocated space you should now see.

However, Win7 often uses all 4 primary partitions allowed on a disk, and if that is the case, you will need to look a bit closer at how you remove one of them.  Choose very carefully, or you could ruin Win7, and I suspect like most users, you will not have an install CD.

Come back again if you need more info or further help.

---

### Post by n9jfg on 2011-08-01
Where does one find this disk management utility ??

Thanks

---

### Post by ajgreeny on 2011-08-02
> **n9jfg said:**
> Where does one find this disk management utility ??

Thanks
Sorry, but I'm not sure.  I don't have windows to even have a look, but I'm sure you will find it with a search of the control center (does windows 7 still have that?)

Google will also help, I'm sure.
[http://ancillotti.hubpages.com/hub/Using-Disk-Management-in-Windows-7-Vista](http://ancillotti.hubpages.com/hub/Using-Disk-Management-in-Windows-7-Vista)

---

### Post by SeijiSensei on 2011-08-02
A little background....

Hard drives can have only four "primary" partitions.  To get around this problem the concept of an "extended" partition with multiple "logical" partitions within it was devised.

I'd suggest repartitioning the hard drive with one primary NTFS partition for Windows and an extended partition for everything else.  In Linux, logical partitions within the extended partition are numbered starting from five.  The first logical partition will be /dev/sda5, the next /dev/sda6, and so on.  There won't be a /dev/sda3 or a /dev/sda4 if you follow this path.

If you've already resized the Windows partition, and it's first on the drive, then just remove any other partitions and dedicate the rest of the drive to a single extended partition.  I'd follow the suggestions you received earlier and set things up like this:

```
/dev/sda1 - Windows
/dev/sda2 - Extended
    /dev/sda5 - Linux root ("/")
    /dev/sda6 - swap (at least equal to your total memory size if 
                you want to use hibernation to disk on a laptop)
    /dev/sda7 - /home

```
I've had no problems using ntfsresize from within gparted on Windows partitions.  However, you must reboot into Windows and let it run chkdsk /f against the edited partition.  As I recall, Windows will do this automatically at boot.  If that doesn't happen, you can force it manually like this:

1)  Start > Programs > Accessories > Command Prompt; open with "Run as Administrator."

2)  At the ">" prompt, type "chkdsk c: /f".

3)  Windows will say it cannot do that at this time because the partition is mounted and ask if you want it to happen at next reboot.  Say OK.

4)  Reboot into Windows; it will report that it's running chkdsk during boot.

---

### Post by linuxforartists on 2011-08-05
Thanks for your help guys!  

In the Windows 7 Start menu, I typed "disk" in the search box and chose "create and format hard disk partitions."  That led me into the Windows disk management tool, where I could check the partitions.

My partitions were unchanged, even after trying to resize them in Pinguy OS then Linux Mint.  When I booted into Windows, it ran the chkdsk file check that SeijiSensei talked about.  Wonder why the partitions didn't resize?  Really weird.

---

